# Controls reference

All combinations on this page are for **firmware V1.0.4**. Verify your firmware in the mobile application under **About** before the first session.

## Mode state machine

```text
   POWER OFF
        │  battery button: one short press, then hold ≥2 s
        │  wait ~1 minute
        ▼
   ZERO TORQUE ─────────── joints are free, the robot is limp
        │                  reachable from any state: L2+Y
        │  L2+B
        ▼
   DAMPING ─────────────── motors are de-energised. A standing robot FALLS
        │  TTS: "Damp mode."  Do not move the joints by hand in this mode
        │                     This is also the EMERGENCY STOP
        │  L2+↑  (Lock Stand)
        ▼
   READY ───────────────── the pose is held, there is no active balancing
        │  TTS: "Ready mode."
        │  R2+A  (Run Control)   or   R1+Y  (Main Operation, 3-DoF waist)
        ▼                             R1+X  (for a 1-DoF waist)
   MOTION ──────────────── active balancing, stick control
        │  TTS: "Walk-around mode activated. Control your speed and stay alert."
        │  left stick — forward/backward · right stick — turn
        │
        ├──► START ─────────── toggle stand ⇄ walk
        ├──► 2×L2 / 2×L1 ───── low / high speed        (in R1+X, R1+Y)
        ├──► R2+↓ / R2+↑ ───── slow / fast run         (in R2+A)
        ├──► R1+arrows ─────── drift compensation      (in R1+X, R1+Y)
        ├──► 2×START ───────── continuous walking — not recommended
        └──► DANCE mode ────── hold the triangle button
                  └─ after the dance → automatically Run mode

   POSTURES (holding L2):
      L2+A → Squat Switch        L2+← → Seated Mode
      L2+X → Lying / Standing    L2+R2 → Debug Mode

   STOPPING LADDER (soft to hard):
      1× START  → stops walking, keeps standing        ← normal stop
      2× START  → interrupts a running action          ← cancel an animation
      L2+B      → Damping, sinks slowly to the floor   ← EMERGENCY
      battery   → only if the robot is suspended or seated  ← last resort
```

## Button combinations

| Action | Combination |
|---|---|
| Power on / off | Battery button: one short press, then **hold ≥2 s** |
| Boot time | **~1 minute** to Zero Torque |
| Zero Torque | ++l2+y++ |
| Damping | ++l2+b++ — from an active state, **hold** the combination rather than tapping it |
| Lock Stand → Ready | **L2+↑** |
| Squat Switch | ++l2+a++ (toggle) |
| Seated Mode | **L2+←** |
| Lying / Standing | ++l2+x++ |
| Debug Mode | ++l2+r2++ — enter while the robot is **suspended and in Damping** |
| Run Control | ++r2+a++ |
| Main Operation Control (1-DoF waist) | ++r1+x++ |
| **Main Operation Control (3-DoF waist — our robot)** | ++r1+y++ — "Only Used For 3-DOF Waist Structure" |
| Stand ⇄ walk | **single press of START** |
| Continuous walking | **double press of START** — not recommended |
| Low / high speed | **2×L2** / **2×L1** (inside R1+X, R1+Y) |
| Slow / fast run | **R2+↓** / **R2+↑** (inside R2+A) |
| Lean forward / backward | hold **START+↑** / **START+↓** |
| Drift compensation | **R1 + arrows** (inside R1+X, R1+Y) |
| Handshake | ++select+a++ (hold SELECT, press A) |
| Wave hand | ++select+y++ |
| Turn around and wave | ++select+x++ |
| **Emergency stop** {: .row-danger } | ++l2+b++{: .kbd-danger } — the robot sinks slowly to the floor |
| Stand up from the floor | ++l2+x++ |
| Dance mode | hold the **triangle** button; start a dance with ++r1+b++ |
| Remote control calibration | ++f1+f3++ → rotate both sticks fully around → ++f3++ to save |

!!! note "Remote control symbols"
    A **triangle** next to a button means hold it. A **star** means a short press.

## Motion modes

| Mode | Entry | Character |
|---|---|---|
| **Main Operation Control** | ++r1+y++ for our robot (3-DoF waist); ++r1+x++ for a 1-DoF configuration | More stable, more assured, noticeably louder |
| **Run Control** | ++r2+a++ | Faster, less stable gait |

Unitree specifies ++r1+y++ for robots with a 3-DoF waist: *"Only Used For 3-DOF Waist Structure"*. Our unit has a 3-DoF waist, so ++r1+y++ is the mode to use.

!!! warning "Continuous walking"
    A double press of START enables Continuous Walking, which Unitree marks as not recommended. Do not confuse it with the single press of START, which stops walking.

## Automatic power-off

The robot powers itself off after **10 minutes** of remote control inactivity.
