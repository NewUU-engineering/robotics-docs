# Robotics Docs

This repository holds the operating and development documentation for the robotics platforms of the NewUU Engineering School. It is written for the people who actually switch the machines on: instructors running lab sessions, students working through the training plan, and developers writing code that runs on the robot.

Every procedure here is written as a procedure. Steps are numbered, button combinations are exact, and safety requirements are marked as such. Follow them in the order given.

The site is available in **English** and **Russian** — switch with the language selector in the header. Use the icon next to it to switch between the light and dark theme.

## Platforms

- **[Unitree G1 EDU](g1/index.md)** — humanoid robot, EDU (secondary development) version. Full operating manual, calibration procedure, SDK and network setup, maintenance and troubleshooting.

## Before you touch a robot

Read **[G1 Safety](g1/safety.md)** first. It is short, and it contains the one thing every operator must know before the robot is powered on: how to stop it.

The emergency stop for the G1 is ++l2+b++. There is no physical emergency stop button on this delivery.

## How the documentation is organised

| Section | Use it when |
|---|---|
| [Overview](g1/index.md) | You need the hardware configuration and the scope of the manual |
| [Safety](g1/safety.md) | Before every session, and during instructor briefings |
| [Controls reference](g1/controls.md) | You need a button combination or the mode state machine |
| [Workspace preparation](g1/workspace.md) | You are setting up the room before a session |
| [Standard operating procedures](g1/operation.md) | You are powering on, walking, gesturing, dancing or shutting down |
| [Working on the gantry](g1/gantry.md) | The robot is suspended for development or calibration |
| [Mobile application](g1/mobile-app.md) | You are using the phone app, OTA updates, navigation or demo teaching |
| [Calibration](g1/calibration.md) | The robot falls repeatedly or drifts and a reboot does not fix it |
| [Development](g1/development.md) | You are writing code, connecting over SSH or extending the hardware |
| [Maintenance](g1/maintenance.md) | You are cleaning, charging or storing the robot |
| [Troubleshooting](g1/troubleshooting.md) | Something is not behaving as documented |
| [Training plan](g1/training-plan.md) | You are teaching students or tracking their progress |

## Contributing

This documentation is maintained in the open. If you find an error or want to add material, open an Issue or a Pull Request.

### Issue rules

1. Check that you are filing in the correct repository.
2. If you are reporting an error, check that no equivalent Issue exists yet.
3. Fill in the title and description precisely.
4. Prefix the title with one of: `[BUG]`, `[PROPOSAL]`, `[QUESTION]`.

### Pull request rules

1. For small changes — typos, formatting — a Pull Request is preferred over an Issue.
2. Describe the problem and your proposed fix. Reference the Issue number where one exists.
3. Before changing formatting, confirm that the change is needed.
4. Follow the prevailing Markdown style of the repository.
5. Documentation is written in English. Keep procedures imperative and unambiguous.

## Local deployment

Run the documentation locally in a Docker container:

```bash
git clone https://github.com/NewUU-engineering/robotics-docs
cd robotics-docs
docker pull squidfunk/mkdocs-material
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
```

Or with a Python virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
pip install mkdocs-material "mkdocs-static-i18n[material]"
mkdocs serve
```

The site is then available at `http://127.0.0.1:8000`.
