# Working on the gantry

The gantry is the safe working position for development, calibration and diagnostics. Use it whenever the robot does not need to be walking on the floor.

## Mounting the robot

| Step | Action |
|---|---|
| 1 | Check which way round the mount is fitted. Mounted the wrong way round, it physically prevents the robot from moving |
| 2 | Raise the robot until the sling is **slightly taut** with the robot in its standing position |
| 3 | Do not lower the robot too far and do not raise it too high. Both are hazardous and neither is prevented in software |
| 4 | Close the sling catches on the gantry |
| 5 | Work **in pairs**: one person steadies and moves the stand, the other operates the remote |

!!! danger "Suspended too high"
    A robot suspended too high and then powered on cannot feel the floor, cannot reach its working stance, and starts extending its legs erratically trying to reach the ground. Keep a finger on **`L2+B`** (Damping). If that does not settle it, power the robot off. This situation is uncommon but likely when working with students.

## Powering on a suspended robot

| Step | Action | TTS |
|---|---|---|
| 1 | Apply power and wait ~1 minute | — |
| 2 | The robot enters Zero Torque **automatically** | — |
| 3 | Press **L2+B** | `Damp mode.` |
| 4 | Run **Lock Stand** (`L2+↑`) | `Ready mode.` |
| 5 | Only now may the robot be lowered or placed on the floor | — |
| 6 | Switch to a working mode (`R2+A` or `R1+Y`) | `Walk-around mode activated…` |

!!! danger "Do not handle the robot before Lock Stand"
    Do not pick the robot up or manipulate its legs before the Lock Stand step. It will go limp and fall.

## Debug mode

**Debug Mode is `L2+R2`.** Enter it while the robot is **suspended and in Damping**. Return to Damping with `L2+B`.

## Standby during development

Leave the robot **suspended on the gantry**, connect the power cable — the indicator turns blue — and switch it to **Zero Torque**. In this state it does not stand under tension and is available for work at any moment.

## Removing the robot from the gantry

1. Pull the robot back slightly.
2. Lift it by hand and clear it from the sling.
3. Remove the catches.

## Why `L2+B` must be held

The asymmetry is deliberate:

- **When powering on,** `L2+B` responds to a single short press.
- **When shutting down, or from an active state,** a single press is not enough — the combination must be **held**.

This prevents an accidental brush against `L2+B` during operation from de-energising the motors and dropping a standing robot.
