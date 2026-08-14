# Safety

Run through this page before every session with students.

## How to stop the robot

There is no physical emergency stop button on this delivery. Stopping the robot is a remote control action, and the correct action depends on the situation.

| Situation | Action | Result |
|---|---|---|
| The robot is walking somewhere you do not want it to go, and the situation is under control | **1× START** | The robot enters Standing: it stops walking and remains standing |
| A dance or gesture is running and must be cut short | **2× START** | The running action is interrupted |
| **Emergency: unpredictable behaviour, risk to people** | **`L2+B`** | Damping mode — the robot **slowly sinks to the ground** |
| The remote control is dead or unresponsive | Battery button | **Only after suspending the robot** with its feet off the ground and at least 2 m of clear space around it. Otherwise it falls flat |

!!! danger "Emergency stop is `L2+B`"
    From the Unitree user manual: *"Emergency Stop: When G1 appears in an unexpected state, press `L2+B`, G1 will enter damping mode and will slowly fall to the ground."*

    Teach this combination to students **first**, before anything else.

### Double START is not an emergency stop

A double press of START interrupts the **action that is currently running**. It stops a dance. It stops a gesture.

If the robot is simply walking and no action is running, there is nothing to interrupt: a double START puts the robot into **Keep stepping** — stepping in place. The robot will not run off, but it will not stop either, and the operator will believe they pressed stop. That false sense of safety is the danger.

- **Emergency stop:** `L2+B`. The robot enters Damping and sinks to the floor.
- **Normal stop:** one press of START. The robot stops walking and stays standing.

### Fall protection

The robot has automatic fall protection: on detecting a fall, the motors switch to braking mode. The chassis is robust. This protection reduces damage — it does not replace correct stopping procedure.

## Safety checklist

| # | Rule |
|---|---|
| 1 | **Emergency stop is `L2+B`** — the robot sinks slowly to the floor. Teach this to students first. The soft stop is a single press of START |
| 2 | **Never activate Damping while the robot is standing unsupported.** Torque is lost instantly and the robot falls. Squat it or suspend it first |
| 3 | **Do not move the robot's joints by hand in Damping mode.** This raises an error |
| 4 | **Do not change wired network settings inside the robot.** Recovering from this requires opening the back panel and reinstalling the operating system |
| 5 | **Do not give a conversational live LLM direct control of the joints** |
| 6 | **Do not suspend the robot too high.** It will not find the floor and will thrash its legs trying to reach it |
| 7 | **Do not touch the LiDAR with your fingers.** Clean it with microfibre only, without pressure |
| 8 | **Do not mix up G1 and Go2 batteries or chargers** |
| 9 | **The remote control is highly sensitive.** Move the sticks smoothly, in small increments |
| 10 | **Walking backwards is unstable.** The robot can fall. Walk backwards only with a spotter or on the gantry |
| 11 | **Before Dance mode, clear the space** and confirm nobody is standing in front of the robot |
| 12 | **Gantry work takes two people** — one steadies and moves the stand, one operates the remote |
| 13 | **Remove or protect the head** before working with a large group |
| 14 | **Do not overtighten long bolts.** Leverage strips the head |
| 15 | **Starting from lying or squatting is allowed only on a flat, hard floor.** With dexterous hands fitted, it is prohibited |
| 16 | **A double press of START is not a stop.** It interrupts a running action; a walking robot is put into stepping in place |
| 17 | **Check the firmware version.** Earlier revisions map these functions to L1 instead of L2 |
| 18 | **The robot powers itself off after 10 minutes** of remote control inactivity. This is normal behaviour, not a fault |
| 19 | **Do not flash the Jetson Orin NX module with third-party images** |
| 20 | **Keep your hands off the joints** — hip and knee — when lifting the robot. They pinch |
| 21 | **Power off only when the robot is suspended or seated, and in Damping.** A standing robot with no support falls flat |
| 22 | **The robot is neither waterproof nor dustproof.** Dry, clean floor only, 0…40 °C |
| 23 | **On tile, gloss and glass, reduce speed** and avoid sharp movements. Do not operate on ice or on soft flooring |
| 24 | **Top speed is 2 m/s.** Keep people well clear |
| 25 | **Do not calibrate on a schedule.** Calibrate on symptoms only, after consulting your supplier |

## What a violation costs

At a competition, a robot fell during a sparring demonstration. Something in its back broke, there was a flash, and the robot never powered on again. The loss was total and irreversible.
