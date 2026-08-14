# Development

## Architecture

```text
   [Developer laptop]  192.168.123.200–250  (static — there is NO DHCP)
            │ Ethernet via the RJ45 on the back panel — the recommended route
            ▼
   ┌────────────────────────┐  Ethernet  ┌──────────────────────────┐
   │  PC2 = Jetson Orin NX  │◄──────────►│  PC1 = control board     │
   │  192.168.123.164       │ (internal) │  192.168.123.161         │
   │  100 TOPS, Ubuntu 20.04│            │  locomotion, balancing   │
   │  ← YOUR CODE RUNS HERE │            │  remote control, app     │
   │  ssh unitree / 123     │            │  DO NOT TOUCH            │
   └────────────────────────┘            └──────────────────────────┘
            │                                        ▲
            │ Livox MID-360 LiDAR                    │ direct radio link
            │ 192.168.123.20                   [remote control]
            ▼
   subnet mask for all hosts: 255.255.255.0
```

The split is a safety feature: if you crash PC2, PC1 keeps running. Locomotion and stabilisation are unaffected, because you never work on PC1 directly.

## Network setup

| Device | IP |
|---|---|
| PC1 — control computer (locomotion) | `192.168.123.161` |
| PC2 — Jetson Orin NX (yours) | `192.168.123.164` |
| Livox MID-360 LiDAR | `192.168.123.20` |
| Your laptop | `192.168.123.200`–`.250` |
| Subnet mask | `255.255.255.0` |

!!! danger "There is no DHCP server on the robot's network"
    Every address is assigned manually. Pick a free address in the `192.168.123.x` subnet, in the range `.200`–`.250`.

### Over Ethernet — recommended

1. Run a cable between your laptop and the RJ45 on the robot's back panel.
2. Network settings → Wired connection → **Manual IPv4** → address `192.168.123.250`, mask `255.255.255.0`.
3. Connect: `ssh unitree@192.168.123.164`, password `123`.
4. Confirm the fingerprint on the first connection.

### Over Wi-Fi

- On older batches, Wi-Fi on the Jetson is not activated. Enable it with `sudo rfkill unblock all`.
- A static IP on the Wi-Fi hotspot removes internet access on the Jetson. Use Ethernet for development.

**Additional hardware** — a second Jetson, a Raspberry Pi and similar — connects through the free RJ45 and joins the same local network as PC1 and PC2.

!!! danger "Never change the wired network settings inside the robot"
    Recovering from a change here means opening the back panel and **reinstalling the operating system**. The interfaces you will see and must leave alone are: Ethernet, the Docker bridge, the bridged LAN and Wi-Fi, and the peer-to-peer LAN.

## SDK

Features land in C++ first, then Python, then ROS2. The ROS2 lag reaches a year.

| Option | When to choose it |
|---|---|
| **`unitree_sdk2`** (C++) | Locomotion control and access to the newest features. The main repository, open source on GitHub, forkable. Pre-installed on the Jetson |
| **Python** | Starting point, integrations, speech. Installed with `pip install` |
| **ROS2** (Cyclone DDS) | Navigation, SLAM, mapping, and attaching third-party modules |

**Use a Python virtual environment.** Working outside one causes dependency conflicts and breaks on OS upgrades.

**Operating system:** Ubuntu 20.04 (the Jetson factory image) or 22.04. The SDK has also been adapted to Fedora Workstation; request that procedure from your supplier.

**Why ROS2 over ROS1 here:** ROS2 shares memory between nodes on **different machines**. Visualisation runs on the laptop while computation runs on the Jetson, inside a single parameter space. Third-party arms attach as a "second robot" in the same ecosystem.

## Develop mode

Once the G1 is powered on, the built-in motion control program starts automatically, even with no input from the remote control. It periodically sends instructions at speed 0. Using the SDK for low-level development in that state causes instruction conflicts, and the robot jitters.

This is also why the robot feels tense in Zero Torque: the built-in program is always running.

!!! danger "Enter Develop mode before any low-level development"
    Skipping this step produces command conflicts and makes the robot shake. Develop mode is available on the EDU version.

| Step | Action | Check |
|---|---|---|
| 1 | Suspend the robot on the gantry and put it into **Damping** | — |
| 2 | Press ++l2+r2++ | Develop mode is entered; the built-in program stops |
| 3 | Press ++l2+a++ | The robot takes a specific diagnostic pose (position mode), confirming Develop mode is active |
| 4 | If the pose is wrong, press ++l2+r2++ again until it is correct | — |
| 5 | Press ++l2+b++ | Back to Damping. You can now work with the SDK |

## High level and low level

| Level | What it is | Risk |
|---|---|---|
| **High level** | Unitree's built-in functions — stand, squat, walk, gestures | Safe |
| **Low level** | Direct joint control across three domains: full body, legs, upper body | **You can physically break the robot** if a joint is not in a valid position. Follow the procedure exactly |

**Locomotion client:** `squat`, `stand up`, `move(X, Y, Z)` — X forward, Y sideways, Z rotation. Motion is two-dimensional; the robot does not walk upward.

**One motor is three motors.** What looks like a single motor from the outside contains three motors internally.

**Where your code runs:** on **PC2 (the Jetson)**. Connecting directly to PC1 is technically possible and is not supported.

## Microphone audio

The SDK does not expose a realtime microphone stream. Audio is synchronised over multicast from PC1 to PC2, one way only.

- Request the multicast group address and port from your supplier.
- Resample the stream to **16 kHz** for most ASR and LLM APIs.

## Simulators and motion learning

| Tool | Status |
|---|---|
| **Isaac Lab** | Recommended for reinforcement learning and imitation learning |
| **Gazebo** | Integration exists and is community-maintained, not official |
| **MuJoCo** | An alternative, weaker for these simulations |

!!! warning "Stairs do not work out of the box"
    Climbing stairs requires retraining locomotion from scratch. The stated maximum step height is about 15 cm. Teams that have achieved stair climbing rewrote the locomotion stack completely.

## AI integration

Use a two-layer architecture:

```text
   [Planner agent]  ──►  breaks the task into steps
   (reasoning model)     and calls the robot's functions
                                  │
                                  ▼
   [VLA — Visual Language Action]  ──►  executes the actions
```

!!! danger "Do not give a conversational live model direct joint control"
    A live conversational model is not reliable enough to control a robot and it makes mistakes. Live APIs are for dialogue, not for control.

- **Function calling:** the model calls predefined robot functions. This requires correct context and prompting.
- **Reference integration:** Google Gemini connected by API key, running locally from a laptop with the robot on Wi-Fi. Fast response comes from **pre-generation** — the model starts generating before the speaker finishes.
- Unitree's world model for household tasks is under development and not yet available.

## Hardware extension

- **Third-party hands** such as the Inspire Robotics hand install plug and play: mount them, route the wiring correctly, and connect them to PC2.
- Only the **U2 configuration (7 DoF arms)** supports external hands. The U1 configuration (5 DoF) has a restricted SDK and does not support these modifications. Our unit is U2.
- Over ROS2 an additional module appears as a "second robot" and is controlled in the same loop.
- The head can be modified: print a front panel on a 3D printer and turn the camera forward — it points downward as standard — or add a second camera.

!!! danger "Do not flash the Jetson Orin NX with third-party images"
