# Calibration

Calibration is the most demanding procedure in this manual. Read it end to end before starting.

## When to calibrate

!!! danger "Do not calibrate on a schedule"
    From the Unitree user manual: *"G1 has been calibrated by default after leaving the factory. **Do not recalibrate the joints for normal use!** If any abnormal situation occurs with the G1, please consult Unitree's official technical support before determining whether joint recalibration is necessary."*

    Calibrate on symptoms, not on the calendar. A routine calibration performed without cause is a regular opportunity to break a working setup.

Calibrate when:

- The robot **falls frequently while walking** and a reboot does not help.
- The robot **drifts consistently to one side** when walking straight. Try remote drift compensation first — `R1 + arrows`.
- The robot has taken a serious fall or impact.

**Agree the calibration with your supplier before starting.** The path in the application is **Settings → Data → Robot → Calibration**.

## The three levels of calibration

| Level | Function |
|---|---|
| **Offset configuration** | Point adjustment of a specific motor's offset by numeric value. Includes a reset |
| **IMU calibration / raw pitch** | Balance adjustment — the robot's forward and backward lean, comparable to setting an artificial horizon |
| **Full body calibration** | Full calibration of every joint, either **assisted** (recommended) or **manual** |

## Preparation

| Step | Action |
|---|---|
| 1 | Put the robot into **Damping**, then power it off completely |
| 2 | Remove the protective body covers if your version has them. Newer versions do not require this |
| 3 | Fit the **mechanical braces** on every joint: waist/torso, legs and **feet** |
| 4 | Tighten the brace screws. When tightening several screws on one part, tighten them **evenly** so the part is not skewed |
| 5 | Fit the **camera brace** |
| 6 | Lock the camera in the application |
| 7 | Level the robot, using the built-in spirit level on the back or the indicator in the application |
| 8 | Connect the charging cable. Calibrating on mains power is normal |

!!! danger "Check the brace on the foot"
    The foot brace is the least visible of the braces and the one most often forgotten. A missing foot brace makes the calibration fail.

!!! warning "Torso brace deactivates the torso motors"
    With the torso brace fitted the robot walks but does not dance.

!!! warning "Do not overtighten long bolts"
    Leverage strips the bolt head. Broken bolts are a recurring failure, including in the hands of Unitree's own engineers.

## Full body calibration (assisted)

| Step | Action | Expected result |
|---|---|---|
| 1 | Application → **Full body calibration** → **Next** | The Development mode screen opens |
| 2 | Choose **Assisted calibration**, not Manual | The robot starts its sweep |
| 3 | The robot drives most of the joints through their range **by itself** | — |
| 4 | **Legs:** raise the leg fully up, then pull it towards you to the opposite stop. Repeat on the second leg | Every joint reaches its **mechanical stop** |
| 5 | **Feet:** rotate the foot to its stop. In its final position the foot must be **perfectly level** | This is the step most often skipped |
| 6 | **Arms:** drive the shoulder, elbow/forearm and wrist to their extreme positions | The wrist ends fully rotated |
| 7 | Press **Calibration / Next** and step away from the robot | — |
| 8 | Wait for the status **`calibration successful`** | — |
| 9 | **Reboot the robot** | — |
| 10 | Remove every brace | — |
| 11 | **Power the robot off and on once more** | The torso is controllable again |

!!! danger "Step 11 is mandatory"
    Without the second power cycle after removing the braces, the torso motors stay deactivated.

!!! note "The rule that governs calibration"
    Every joint must be driven to its **full mechanical stop**.

Assisted mode does not drive every joint automatically — some must be driven by hand. It is still far simpler than manual calibration.

## Success criteria

After the reboot, switch to a working mode and confirm all of the following:

- The robot rises into its working stance **by itself**, with no manual help.
- It stands **centred and level**, without trembling.
- Its **feet do not catch the floor**.
- Rocked forward and backward, it does not fall — it balances itself.
- Walking straight, it **does not drift sideways**.
- The application shows no flashing red indicator.

## Known failure mode

| Stage | Detail |
|---|---|
| **Symptom** | After calibration: a flashing red indicator and the error `Communication, joint over limit` |
| **Cause** | A brace was left on the foot. Assisted mode could not drive that joint to its stop, so the left and right legs ended up with **different zero points** |
| **Fix** | Free and level the feet, then repeat the full body calibration from the start |
| **Result** | The calibration succeeds and the robot is measurably more stable |

Two hypotheses commonly raised for this symptom are wrong and waste time: the order of operations around Lock Stand, and a low battery charge. Check the braces first, starting with the feet.
