# Rollback
This is the PREVIEW repo (launchriot-gareth-next). The live site (launchriot-winterhalter, gareth.launchriot.online) is NOT touched by anything here.
Preview rollback: git revert to the previous commit and push. No CNAME, DNS or MX are used in this repo.
Commits: 5381c24 (feature 1 screens), 84e7461 (event reschedule fix), plus later head fix. Revert any with: git revert --no-edit <hash> && git push
Feature 2 (contacts.js: Contacts + Follow-ups screens; theme.css additions; app.js accepts session id in login body): revert with git revert --no-edit <hash> && git push. Live site untouched.
Feature 3 (documents.js: Documents + Search screens): revert with git revert --no-edit <hash> && git push. Live site untouched.
Feature 4/5 (projects.js: Projects, Activity feed, Home dashboard; app.js exports greet): revert with git revert --no-edit <hash> && git push. Live site untouched.
Follow-up fixes (nav.js grouped navigation + mobile bottom bar, search hits open the exact item, mobile Capture button clears the bottom bar/footer): revert with git revert --no-edit <hash> && git push. Live site untouched.
