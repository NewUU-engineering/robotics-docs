# robotics-docs

Operating and development documentation for the robotics platforms of the NewUU Engineering School.

📖 **[Read the documentation](https://newuu-engineering.github.io/robotics-docs/)**

## Contents

- **Unitree G1 EDU** — the full operating manual: safety, controls reference, workspace preparation, standard operating procedures, gantry work, the mobile application, calibration, SDK development, maintenance, troubleshooting and the student training plan.

The documentation is written in English, as procedures. Steps are numbered, button combinations are exact, and safety requirements are marked as such.

## Reporting problems and proposing improvements

If you find an error in this documentation or want to propose an improvement, open an [Issue or a Pull Request](https://docs.github.com/desktop/contributing-and-collaborating-using-github-desktop/creating-an-issue-or-pull-request).

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
5. Write in English, and keep procedures imperative and unambiguous.

## Local deployment

### In a Docker container

```bash
git clone https://github.com/NewUU-engineering/robotics-docs
cd robotics-docs
docker pull squidfunk/mkdocs-material
docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
```

### In a Python virtual environment

```bash
git clone https://github.com/NewUU-engineering/robotics-docs
cd robotics-docs
python3 -m venv venv
source venv/bin/activate
pip install mkdocs-material
mkdocs serve
```

The site is then available at `http://127.0.0.1:8000`.

## Publishing

Pushes to `main` trigger the `Deploy Docs` workflow, which runs `mkdocs gh-deploy --force` and publishes the site to GitHub Pages from the `gh-pages` branch.
