
## Session: Oct 17 2026, 1:40 pm ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office push alerts merged to main (b014a27) and deployed by CLI; Yeti's iPhone test push worked
- 4 crew setup videos (iPhone/Android x EN/ES), HyperFrames, drawn screens, Chris VO: on-point-jd/social/video/onpoint-alerts-setup/renders/final/
- Office help clip "Text the team and see who got it" recorded in onpoint-office (uncommitted)

**What's live / deployed:**
- app.onpointjd.com at b014a27 with alerts; VAPID keys in Vercel; migration on live DB

**Next up:**
- Text the videos to the team; commit + deploy the help clip; website skip-pushed-phones change; group texts as push

**Notes for other environments:**
- onpoint-office has NO Git auto-deploy: deploy with `vercel deploy --prod`