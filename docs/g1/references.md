# References

## Official Unitree documentation

- **[G1 User Manual — official Unitree PDF](https://cistemlabs.ai/wp-content/uploads/2025/04/G1-USER-MANUAL-EN.pdf)** — emergency stop, environment requirements, battery runtime, speed, calibration policy, Develop mode, shutdown procedure.
- [Controls (Firmware V1.0.4) — Unitree G1 Docs](https://docs.quadruped.de/projects/g1/html/operation_1.4.html) — the complete combination table, the startup chain, and the emergency stop.
- [Controls (Firmware V1.0.2)](https://docs.quadruped.de/projects/g1/html/operation_1.2.html) — the earlier L1-based layout.
- [Overview — Unitree G1 Docs](https://docs.quadruped.de/projects/g1/html/g1_overview.html) — Livox MID-360, RealSense D435i, and the DoF of each configuration.
- [Unitree G1 Developer Guide](https://support.unitree.com/home/en/G1_developer) — the official developer portal.
- [G1 Development Guide — Weston Robot](https://docs.westonrobot.com/tutorial/unitree/g1_dev_guide/) — IP addresses, credentials, and Debug mode.
- [Motion — unitreerobotics/xr_teleoperate Wiki](https://github.com/unitreerobotics/xr_teleoperate/wiki/Motion) — the L1-to-L2 layout change and ++r1+x++ for a 1-DoF waist.
- [Unitree G1 — Robotics Knowledgebase](https://roboticsknowledgebase.com/wiki/common-platforms/unitree-g1/) — FSM 500 / 501 / 801 and the ++r1+x++ / ++r1+y++ / ++r2+a++ mapping.

## Software

- [`unitree_sdk2`](https://github.com/unitreerobotics/unitree_sdk2) — the main C++ SDK.
- [`unitree_sdk2_python`](https://github.com/unitreerobotics/unitree_sdk2_python) — the Python bindings.
- [Isaac Lab](https://isaac-sim.github.io/IsaacLab/) — reinforcement learning and imitation learning.

## Maintaining this manual

This manual documents firmware **V1.0.4**. When the robot is updated, verify the button layout against the legend printed on the remote and against the Unitree documentation for the new firmware version, then update the [controls reference](controls.md) accordingly.

Report errors and submit corrections through the [repository](https://github.com/NewUU-engineering/robotics-docs).
