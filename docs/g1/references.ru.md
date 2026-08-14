# Источники

## Официальная документация Unitree

- **[G1 User Manual — официальный PDF Unitree](https://cistemlabs.ai/wp-content/uploads/2025/04/G1-USER-MANUAL-EN.pdf)** — аварийная остановка, требования к среде, ресурс батареи, скорость, политика калибровки, Develop mode, порядок выключения.
- [Controls (Firmware V1.0.4) — Unitree G1 Docs](https://docs.quadruped.de/projects/g1/html/operation_1.4.html) — полная таблица комбинаций, стартовая цепочка и аварийная остановка.
- [Controls (Firmware V1.0.2)](https://docs.quadruped.de/projects/g1/html/operation_1.2.html) — прежняя раскладка на L1.
- [Overview — Unitree G1 Docs](https://docs.quadruped.de/projects/g1/html/g1_overview.html) — Livox MID-360, RealSense D435i и степени свободы по конфигурациям.
- [Unitree G1 Developer Guide](https://support.unitree.com/home/en/G1_developer) — официальный портал для разработчиков.
- [G1 Development Guide — Weston Robot](https://docs.westonrobot.com/tutorial/unitree/g1_dev_guide/) — IP-адреса, учётные данные и Debug mode.
- [Motion — unitreerobotics/xr_teleoperate Wiki](https://github.com/unitreerobotics/xr_teleoperate/wiki/Motion) — смена раскладки с L1 на L2 и `R1+X` для талии на 1 DoF.
- [Unitree G1 — Robotics Knowledgebase](https://roboticsknowledgebase.com/wiki/common-platforms/unitree-g1/) — FSM 500 / 501 / 801 и соответствие `R1+X` / `R1+Y` / `R2+A`.

## Программное обеспечение

- [`unitree_sdk2`](https://github.com/unitreerobotics/unitree_sdk2) — основной SDK на C++.
- [`unitree_sdk2_python`](https://github.com/unitreerobotics/unitree_sdk2_python) — привязки для Python.
- [Isaac Lab](https://isaac-sim.github.io/IsaacLab/) — reinforcement learning и imitation learning.

## Поддержка руководства

Руководство описывает прошивку **V1.0.4**. После обновления робота сверьте раскладку кнопок с легендой на пульте и с документацией Unitree для новой версии прошивки, затем обновите [справочник по управлению](controls.md).

Об ошибках сообщайте и правки присылайте через [репозиторий](https://github.com/NewUU-engineering/robotics-docs).
