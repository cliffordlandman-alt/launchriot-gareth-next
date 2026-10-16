# Rollback
This is the PREVIEW repo (launchriot-gareth-next). The live site (launchriot-winterhalter, gareth.launchriot.online) is NOT touched by anything here.
Preview rollback: git revert to the previous commit and push. No CNAME, DNS or MX are used in this repo.
Commits: 5381c24 (feature 1 screens), 84e7461 (event reschedule fix), plus later head fix. Revert any with: git revert --no-edit <hash> && git push
Feature 2 (contacts.js: Contacts + Follow-ups screens; theme.css additions; app.js accepts session id in login body): revert with git revert --no-edit <hash> && git push. Live site untouched.
Feature 3 (documents.js: Documents + Search screens): revert with git revert --no-edit <hash> && git push. Live site untouched.
Feature 4/5 (projects.js: Projects, Activity feed, Home dashboard; app.js exports greet): revert with git revert --no-edit <hash> && git push. Live site untouched.
Follow-up fixes (nav.js grouped navigation + mobile bottom bar, search hits open the exact item, mobile Capture button clears the bottom bar/footer): revert with git revert --no-edit <hash> && git push. Live site untouched.

## PROMOTE TO LIVE (NOT EXECUTED. Needs Clifford's explicit approval)
Preview repo: launchriot-gareth-next (cliffordlandman-alt.github.io/launchriot-gareth-next). Live repo: launchriot-winterhalter (gareth.launchriot.online). Nothing below has been run.
1. Tag the preview commit being promoted: `git tag promote-YYYYMMDD <hash> && git push --tags` (the last tested commit; see the report).
2. Back up live first: in a clean clone of launchriot-winterhalter run `git tag pre-workspace-YYYYMMDD && git push --tags`. Record the current live HEAD hash in this file.
3. Check the API allows the live origin: `OPTIONS` from https://gareth.launchriot.online must return 204 with authorization and content-type allowed (Khalid confirmed this origin is listed). Cookie login still works there; the Bearer session also works.
4. Copy the preview files (index.html, app.js, workspace.js, contacts.js, documents.js, projects.js, nav.js, decisions.js, vips.js, staff.js, notes.js, meetprep.js, exec.css, theme.css, brand-logo.png, launchriot-logo.png) into the live repo root. Do NOT copy CNAME, KHALID.md or ROLLBACK.md, and do not touch DNS or MX. Keep the live CNAME file as is. Logo files are copied byte for byte.
5. Commit and push to the live repo. Wait for Pages to finish, then smoke test on https://gareth.launchriot.online at 390 and 1440: sign in, Home loads, add and delete one task, open Contacts, Documents, Search, Activity. Delete the test rows afterwards.
6. Tell Clifford and Chief it is live. Nothing is announced to Gareth until Clifford says so.

## REVERT LIVE (if anything is wrong after promotion)
- Fast: in the live repo `git revert --no-edit <promotion commit> && git push` (restores the previous site; Pages redeploys in about a minute).
- Hard fallback: `git checkout pre-workspace-YYYYMMDD -- . && git commit -m "Restore previous site" && git push`.
- Data is not affected by either: all workspace data lives in the API, not in the site files. Nothing needs to be deleted.
- Preview repo: revert any commit with `git revert --no-edit <hash> && git push` (see the lines above).
