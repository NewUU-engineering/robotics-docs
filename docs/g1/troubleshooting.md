# Troubleshooting

## Motion and stability

| Symptom | Cause | Action |
|---|---|---|
| The robot **drifts sideways** when walking straight | A small offset. This usually clears without calibration | **First:** apply drift compensation from the remote — **`R1 + arrows`** inside Main Operation Control (++r1+x++ / ++r1+y++). **If that fails:** run [full body calibration](calibration.md) |
| After calibration the robot **does not stand up by itself** and has to be helped by hand | The calibration did not complete correctly — not every joint reached its stop | Repeat the calibration, driving **every** joint to its mechanical stop |
| Flashing red in the application, `Communication, joint over limit` | A joint is outside its permitted range. During calibration this means a brace was left on, most often **on the foot** | Free and level the feet, then repeat the calibration from the start |
| **The torso does not move** and dances do not run | The torso brace is fitted, or the robot was not rebooted after removing it | Remove the brace, then **power the robot off and on** |
| The robot **fell while being handled by hand** | Lock Stand was not run before the physical intervention | Press `L2+↑` before touching the robot |
| The robot **does not balance after Lock Stand** | Ready mode holds the pose without active balancing. This is normal behaviour | Move to a working mode immediately (++r2+a++ / ++r1+y++) and provide support |
| The robot **fell when started from lying** | Starting from lying or squatting is allowed only on a flat, hard floor, and is prohibited with dexterous hands fitted | Move to a flat, hard floor, or lift the robot manually from the gantry |

## Power and shutdown

| Symptom | Cause | Action |
|---|---|---|
| The robot **powered off by itself** with no input | Automatic power-off after 10 minutes of remote control inactivity | Normal behaviour. Power it back on |
| The robot **fell while being powered off** | ++l2+b++ was pressed without support, or without holding the combination | Squat the robot (++l2+a++) or suspend it first, and **hold** ++l2+b++ |
| The robot **fell flat during shutdown** | It was powered off standing, with no support | Always power off suspended or seated, and in Damping |
| The robot **lay down on its own** | The battery ran out | Normal behaviour. Pick it up and put it on charge |

## Remote control

| Symptom | Cause | Action |
|---|---|---|
| **Buttons do not do what this manual describes** | Firmware older than V1.0.4 maps these functions to ++l1++ | Check the version in the application under About. On older firmware: Zero Torque ++l1+b++, Damping ++l1+a++, Lock Stand `L1+↑` |
| **The remote behaves erratically**, the sticks drift | The **joystick** calibration has drifted, not the robot's | ++f1+f3++ → rotate both sticks fully around several times → ++f3++ to save |
| **The remote does not bind** | The remote's code has not been entered | Application → Settings → Remote Control Settings → enter the remote's code. The **DL** indicator lights when the link is established |

## Gantry

| Symptom | Cause | Action |
|---|---|---|
| The robot **thrashes and cannot stand** while suspended | It is suspended too high and cannot find the floor | Press ++l2+b++ (Damping). If that does not settle it, cut the power |
| The robot **does not move** on the gantry | The mount is fitted the wrong way round | Refit the mount |

## Application and connectivity

| Symptom | Cause | Action |
|---|---|---|
| **Android does not connect** to the robot | Priority mode switches the phone to mobile data | Disable automatic switching or mobile data, or use a different phone |
| **The application does not connect over AP** | The access point name contains special characters or spaces, or the phone is too far away | Rename the access point, move the phone closer, restart the robot and the application |
| **Firmware does not update** | The robot is in AP mode | Switch to Wi-Fi mode and enable the OTA box |
| **The voice assistant does not respond** | No Wi-Fi, or the balance has not been topped up | Check Wi-Fi and the account balance (from $15) |
| **The wrong map** in Navigation | A map from another robot, for example a Go2, is open | Check which robot the map belongs to and recreate it if necessary |
| The robot **stopped along the route** | An obstacle was detected: `There are obstacles in your way` | Normal behaviour. Clear the obstacle. The robot stops rather than routing around it |

## Development

| Symptom | Cause | Action |
|---|---|---|
| **The SDK does not see the robot** | The devices are not on the same local network. There is no DHCP on the robot's network | Confirm the laptop has a static address in `192.168.123.200`–`.250` with mask `255.255.255.0`, and that `192.168.123.164` responds to ping |
| **The Jetson has no internet** over Wi-Fi | A static IP is set on the Wi-Fi hotspot | Switch to Ethernet for development |
| **The robot feels tense in Zero Torque** and jitters under SDK control | The built-in motion control program always runs and sends speed-0 commands, which conflict with yours | Enter [Develop mode](development.md#develop-mode) — ++l2+r2++ while suspended and in Damping |

## Anything else

Run **Log retrieval** → **Log upload** in the application and report the issue to your supplier's support channel.
