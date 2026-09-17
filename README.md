# python-jenkins-freestyle-demo

Minimal Python project for testing a Jenkins **Freestyle** build.

## Contents
- `app.py` — sample code
- `test_app.py` — pytest tests
- `requirements.txt` — dependencies

## Local check
```
pip install -r requirements.txt
pytest -v
```

## Jenkins Freestyle job setup
1. New Item → Freestyle project → name it, OK.
2. Source Code Management → Git → paste this repo's URL (push it to GitHub/GitLab first).
3. Build Triggers → check "GitHub hook trigger" or "Poll SCM" (`H/5 * * * *`) if you want auto-builds.
4. Build → Add build step → Execute shell:
   ```
   python3 -m venv venv
   . venv/bin/activate
   pip install -r requirements.txt
   pytest -v --junitxml=results.xml
   ```
5. Post-build Actions → Publish JUnit test result report → set `results.xml`.
6. Save → Build Now.

Ensure the Jenkins agent has Python 3 installed, or select a node/label that does.
