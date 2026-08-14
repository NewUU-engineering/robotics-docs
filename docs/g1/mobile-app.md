# Mobile application

## Connecting

| Step | Action |
|---|---|
| 1 | Power the robot on and wait for it to boot |
| 2 | The robot raises a **Wi-Fi access point (AP mode)**. This is the default and the recommended mode |
| 3 | Connect the phone to that access point |
| 4 | Open the application and press **Start** |

### AP mode and Wi-Fi mode

| Mode | When to use it |
|---|---|
| **AP mode** — the robot is the access point | The default, and correct for nearly all work |
| **Wi-Fi mode** — the robot joins an external network | Firmware updates (OTA) and remote diagnostics by a support engineer |

!!! warning
    Firmware updates are unavailable in AP mode. Switch to Wi-Fi mode to update.

### Android connection issue

**Symptom:** the connection is stable on iOS, while on Android the robot periodically fails to connect.

**Cause:** many Android devices enable *priority mode*, which switches the system to mobile data when the Wi-Fi signal is weak and drops the link to the robot's access point.

**Fix:**

1. Disable automatic switching to mobile data in the network settings.
2. Or switch mobile data off for the duration of the session.
3. On devices where that setting is unavailable — this occurs on some Samsung models — use a different phone.

Keep the application installed on **several phones**. Three, including a spare Android device, is a workable arrangement.

## Application sections

| Section | Function |
|---|---|
| **Body Info** | Communication quality (%), location of body parts, temperature and air cooling |
| **Calibration** | Full body calibration (assisted and manual), offset configuration, IMU calibration, slow reach. See [Calibration](calibration.md) |
| **Peripheral** | Remote control charge, rebinding a new remote, individual button tests, audio functions |
| **Update / Service** | Log retrieval and log upload, alarm information, service status, **OTA box** |
| **Security** | Internet remote connection — see the warning below |
| **About** | Serial number, software and hardware versions, firmware update, feedback |
| **Guide** | Video tutorials and the user manual. Covers startup and shutdown, posture and movement, debug mode, both calibration types, network connection, remote control timing, navigation. The manual is in English; request the Russian version from your supplier |
| **Motion marketplace** | Downloadable community motions and dances, including a side flip. Do not run advanced motions such as the side flip on an untested robot |
| **Demo teaching** | Kinaesthetic gesture teaching — see below |
| **Navigation** | LiDAR mapping and patrolling — see below |
| **Audio / AI Voice** | Wake-up conversation mode and the Doubao assistant — see below |
| **Locks** | Separate switches to lock the **camera** and the **torso**. Both are needed during calibration |
| **Settings** | Interface language, including Uzbek, and the 3D room view |

**Camera:** the application takes photos and video. Video is capped at **30 seconds with an automatic stop** — there is no need to press stop.

!!! danger "Internet remote connection"
    With this feature enabled, anyone signed in **under the same account** can connect to the robot from an external network and control it after you leave the local session. Enable it only deliberately and with a clear reason.

## Firmware updates (OTA)

1. Enable the **OTA box** in the Services section in advance. Without it, no update notifications arrive.
2. Wait for the new-firmware notification. Unitree releases updates roughly every 2–3 months.
3. Switch the robot to **Wi-Fi mode**. Updates are blocked in AP mode.
4. Start the update from the About section.

## Demo Teaching

| Step | Action |
|---|---|
| 1 | Open **Demo teaching** → **Create teaching** |
| 2 | Press **Start teaching** |
| 3 | Guide the robot physically through the movement by hand |
| 4 | Press **Stop** → **Save** and give the gesture a name |

**Scope:** teaching covers the **upper body only** — torso and arms. The legs do not participate.

!!! warning
    Holding the robot unevenly during teaching skews the torso. Move the limbs smoothly and symmetrically.

## Navigation

| Step | Action |
|---|---|
| 1 | Put the robot into running or regular mode |
| 2 | Open **Navigation** and create a map, giving it a name |
| 3 | Walk the robot through the space. The LiDAR builds a **3D scan** |
| 4 | Press **Mark patrol point** to mark a route point |
| 5 | Press **Executable task** to assign an action at that point — photo or video |
| 6 | Repeat for the remaining points and **connect the points** into a route |
| 7 | Press **Save** and start the route |

**On encountering an obstacle** the robot announces `There are obstacles in your way. Please be careful.` and **stops**. Plan on the robot stopping: clear the route before running a patrol.

!!! warning "Check which map is open"
    Maps from different robots sit side by side in the application. A map recorded by a Go2 quadruped looks much like a G1 map in the list. Confirm which robot a map belongs to before using it.

## Doubao voice assistant

**Wi-Fi is required.** The assistant supports English and Chinese.

| Step | Action |
|---|---|
| 1 | Open **Audio** and enable **Wake up conversation mode** |
| 2 | Say the wake word followed by a command, for example "Hello robot", "Go forward" |
| 3 | The assistant replies, executes commands and plays music |

**Billing:** this is a paid service. The starting balance is from **$15**, topped up through the Unitree website by the customer.

**Alternative:** connect your own LLM through an API key. See [AI integration](development.md#ai-integration).

## Logs and diagnostics

Errors appear in red in the application. To send them to support:

1. Run **Log retrieval**.
2. Run **Log upload**.

Logs are not stored on the phone — they go straight to the Unitree cloud, where engineers analyse them.
