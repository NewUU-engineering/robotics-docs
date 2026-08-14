# Unitree G1 EDU — Overview

This is the operating manual for the Unitree G1 EDU humanoid robot as delivered to the NewUU Engineering School. It covers startup, motion control, calibration, the mobile application, SDK development, maintenance and troubleshooting.

!!! danger "Read the safety page first"
    The emergency stop is ++l2+b++. There is no physical emergency stop button on this delivery. Read **[Safety](safety.md)** before powering the robot on, and brief every new operator on it.

## Firmware scope

This manual documents **firmware V1.0.4**. Check your firmware version in the mobile application under **About** before the first session.

!!! warning "Firmware earlier than V1.0.4"
    Firmware versions before V1.0.4 use ++l1++ where V1.0.4 uses ++l2++: Zero Torque is ++l1+b++, Damping is ++l1+a++, Lock Stand is `L1+↑`. Every combination in this manual assumes V1.0.4.

## Source precedence

When sources disagree, use them in this order:

1. **The legend printed on the remote control itself.** Unitree's documentation directs operators to this legend as the primary reference.
2. **Official Unitree documentation for your firmware version.**
3. **This manual.**
4. **Your supplier**, for anything the first three do not settle.

## Delivered hardware configuration

| Component | Specification |
|---|---|
| Model | Unitree G1, **EDU version** (secondary development) |
| Configuration | **U2** — 3 DoF waist, 7 DoF arms |
| PC1 | Control board. Runs locomotion, stabilisation, and the links to the remote control and the mobile application. Not user-accessible |
| PC2 | **NVIDIA Jetson Orin NX, 100 TOPS**, Ubuntu 20.04 factory image. Fully available for your code |
| PC1 ↔ PC2 | Ethernet cable inside the robot |
| Head | **Intel RealSense D435i** depth camera and **Livox MID-360** LiDAR (360° horizontal, 59° vertical). The LiDAR cable detaches from the board; the head is removed with a **Torx** driver, not a hex key |
| Ports | 4× USB Type-C (one carries DisplayPort), battery power output, pin header for boards such as a Raspberry Pi, 2× RJ45 |
| Battery | Indicator segments of 25% each. 5 V charger. **Not interchangeable with the Go2 battery** |
| Spirit level | Fitted on the back of newer batches. Used to level the robot during calibration |
| Gantry | Stand with a winch and sling. The robot can walk while suspended |
| Calibration braces | Mechanical stops for waist/torso, legs and **feet**, plus a camera brace. The Go2 set is separate |
| Included tools | T-handle driver and pliers |
| Remote controls | Two units in the case — one for the G1 and one for the Go2, labelled. All button combinations are printed on the remote |
| Emergency stop button | **Not fitted.** The distributor adds it only to turnkey solutions for the EU and US markets |

!!! note "Batch differences"
    Delivery batches differ. Newer units have a quieter and more stable head, a voice output at roughly half the volume, Wi-Fi enabled on the Jetson out of the box, a spirit level for calibration, and a different Jetson board and GPIO revision. Verify the configuration of your own unit rather than relying on a general description.

!!! warning "Certification"
    Robots in this delivery do not carry European certification as delivered. The large red button on top is fitted by the distributor only for turnkey products sold into the EU and US markets.

## Reading order

New operators should work through the manual in this order:

1. [Safety](safety.md) — how to stop the robot, and the full safety checklist.
2. [Controls reference](controls.md) — the mode state machine and the complete button table.
3. [Workspace preparation](workspace.md) — environment requirements and the pre-session checklist.
4. [Standard operating procedures](operation.md) — power-on through shutdown.
5. [Working on the gantry](gantry.md) — the safe working position for everything else.

Developers continue with [Development](development.md). Instructors should also read [Calibration](calibration.md) and [Training plan](training-plan.md).
