# Standard operating procedures

Every procedure on this page assumes firmware V1.0.4 and a workspace prepared according to [Workspace preparation](workspace.md).

## Power-on sequence

**Precondition:** the battery is fitted, the space around the robot is clear, and the robot is lying down or standing with support.

!!! danger "Starting from lying or squatting"
    Start the robot from a lying or squatting position **only on a flat, hard floor**. With dexterous hands fitted, starting from lying or squatting is prohibited.

| Step | Action | Result |
|---|---|---|
| 1 | Press the battery button **once, briefly** | The indicator lights up |
| 2 | Press the same button again and **hold for ≥2 seconds** | Boot starts |
| 3 | **Wait ~1 minute.** Do not touch the robot | — |
| 4 | The robot enters **Zero Torque mode** automatically | Joints are free, the arms hang loose |
| 5 | Press ++l2+b++ | TTS: `Damp mode.` — the robot is in Damping |
| 6 | Press **L2+↑** (Lock Stand) | TTS: `Ready mode.` — the pose is locked |
| 7 | Press ++r2+a++, or ++r1+y++ for our 3-DoF configuration | TTS: `Walk-around mode activated…` — the robot is ready to move |

!!! danger "Do not move the joints by hand in Damping mode"
    Moving the joints manually while the robot is in Damping raises an error.

!!! danger "Do not run step 7 until the robot is stable"
    Move to the working mode only once the robot stands steadily or is suspended. Ready mode holds the pose but does not balance actively.

## Standing up from the floor

**Precondition:** the robot is lying down, in Zero Torque or Damping.

!!! danger
    Stand the robot up **only on a flat, hard floor**. With dexterous hands fitted, standing up from lying is prohibited.

Both starting positions work: the robot lying flat on its back in a correct pose, and the robot lying in an arbitrary, tangled pose.

| Step | Action |
|---|---|
| 1 | Confirm that nobody is within arm's reach |
| 2 | Press ++l2+x++ — Lying and Standing switches between the lying and standing positions |
| 3 | TTS: `Robot rising. Please stand clear.` — step back |
| 4 | TTS: `Walk-around mode activated. Control your speed and stay alert.` |

## Walking

!!! danger "The remote control is highly sensitive"
    Move the sticks smoothly, in small increments.

| Control | Function |
|---|---|
| **Left stick** | Walk forward / backward |
| **Right stick** | Turn left / right |
| ++start++ | Toggle stand ⇄ walk |
| **2×L2 / 2×L1** | Low / high speed (inside R1+X, R1+Y) |
| **R2+↓ / R2+↑** | Slow / fast run (inside R2+A) |
| **Hold START+↑ / START+↓** | Lean the body forward / backward |
| **R1 + arrows** | Drift compensation — see [Troubleshooting](troubleshooting.md) |

### Behaviour

- **Walking backwards is unstable and the robot can fall.** This is a limitation of the current locomotion algorithm, not a fault of the unit. Walk backwards only with a spotter or on the gantry.
- The robot withstands a light push from the side. It compensates and stays upright.
- If the robot starts drifting sideways, correct it with the forward stick — it will recover balance. Systematic drift calls for [drift compensation](troubleshooting.md), and if that does not resolve it, [calibration](calibration.md).

### Why the gait looks unusual

Earlier locomotion training used a "virtual point" that pulled the robot forward, and the robot pushed back against it. The current version adds the model's **weight** in simulation and pushes it instead. The gait is more natural as a result, but the robot sits down slightly when moving backwards as it works to stay upright.

## Interactive gestures

**Precondition:** the robot is standing in a working mode.

| Step | Action |
|---|---|
| 1 | Turn the robot to face the person, using the right stick |
| 2 | **Hold SELECT** and press the gesture button |
| 3 | The robot performs the gesture |
| 4 | **Press the same combination again** — the arm returns to its starting position |

| Gesture | Combination |
|---|---|
| Handshake | **SELECT + A** |
| Wave hand | **SELECT + Y** |
| Turn around and wave | **SELECT + X** |

Gestures do not affect balance. The robot keeps standing steadily throughout.

## Dance mode

!!! danger "The most hazardous of the basic demonstrations"
    The robot makes wide, sweeping movements and can strike a person.

| Step | Action |
|---|---|
| 1 | **Clear at least 3 m in every direction** |
| 2 | Confirm that nobody is standing in front of the robot |
| 3 | **Hold** the button marked with a triangle. A short press is not enough |
| 4 | TTS: `Entering dance mode.` |
| 5 | Start a dance with ++r1+b++ |
| 6 | TTS: `Please keep a safe distance.` |
| 7 | When the dance ends, the robot switches to **Running mode** automatically |

**To stop a dance:** double press ++start++. This interrupts the running action.

!!! danger "Double START is not an emergency stop"
    A double press of START interrupts the action that is running. If the robot is walking with no action running, it goes into stepping in place instead of stopping. The emergency stop is ++l2+b++; the normal stop is a single press of START. See [Safety](safety.md).

!!! warning "Torso brace"
    Dances do not run while the torso brace is fitted — the torso motors are deactivated. See [Calibration](calibration.md).

## Squat, stand and seating

**Squat/Stand is a toggle:** the same combination ++l2+a++ works in both directions.

| Situation | Result |
|---|---|
| **Robot on the floor**, ++l2+a++ pressed | It squats → TTS `Robot squatting. Please be careful.` → `Damp mode.` — **Damping engages automatically** |
| **Robot on the gantry**, ++l2+a++ pressed | It squats, but **Damping does not engage automatically**. Switch to Damping manually |

### Seating on a chair

1. Place a chair of suitable height **behind** the robot.
2. Press **`L2+←`** for Seated Mode.
3. **Provide support from behind.** The robot is not fully stable in this state.
4. To stand up, press **`L2+↑`** (Lock Stand → Ready), then ++r2+a++.

!!! danger "Lock Stand holds the pose without balancing"
    In Ready mode the robot stands in a fixed pose with no active balancing, and it falls if pushed. This is an intermediate state — do not leave the robot in it unattended. Move to a working mode immediately.

## Shutdown

| Step | Action |
|---|---|
| 1 | Put the robot into **Squat** (++l2+a++), or suspend it on the gantry |
| 2 | Confirm the robot is in **Damping mode**. On the floor this engages automatically; on the gantry, hold ++l2+b++ to engage it manually |
| 3 | Press the battery button: **one short press, then one long press** |

!!! danger "Damping before shutdown is mandatory"
    The robot must be in Damping before power-off. Zero Torque is not required. Power off only when the robot is suspended or seated — a standing robot with no support falls flat.

**If the battery runs out during operation,** the robot folds down on its own. No special action is required: pick it up and put it on charge.

**During long idle periods,** switch the robot into Damping periodically so that it does not stand under tension for weeks.
