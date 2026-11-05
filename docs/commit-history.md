# Suggested Commit History

Run these in the repo folder, one commit at a time.

```
git init
git branch -M main

git add LICENSE .gitignore
git commit -m "Add license and gitignore"

git add docs/images/topology.png
git commit -m "Add network topology diagram"

git add configs/
git commit -m "Add captured router configurations"

git add verification/captured-outputs/01_* verification/captured-outputs/02_* verification/captured-outputs/03_* verification/captured-outputs/04_*
git commit -m "Add routing tables before redistribution"

git add verification/captured-outputs/05_* verification/captured-outputs/06_* verification/captured-outputs/07_* verification/captured-outputs/08_* docs/images/screenshots/
git commit -m "Add post-redistribution routing tables, pings and screenshots"

git add verification/commands.md lab/
git commit -m "Add verification commands and lab folder"

git add README.md docs/
git commit -m "Add README and documentation"

git remote add origin https://github.com/mushfiq11235/Enterprise-Route-Redistribution-Design.git
git push -u origin main
```
