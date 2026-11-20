## Session: 2026-11-20 ET
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry (State Farm): transcribed all 11 archived reels and wrote a compliance read: ~/Archive/Clients/Sam-Insurance/compliance-review-2026-11-20.md (transcripts beside it). Only 4 of 10 scripts are evergreen; six are spring or summer dated. Red hoodie Intro retired (Red Wings logo).
- Built Sam's client portal: https://samquisenberry.vercel.app, code ~/Projects/sam-portal. Sam picks one of 10 HeyGen looks per topic row (drag or tap), edits topic and script, ticks "OK to make". The tick locks the row, stores the exact approved text and time, and assigns the next free Tuesday.
- Loaded 11 scripts as drafts: the 4 evergreen reels with the flagged lines fixed, plus 7 new winter ones.
- Mac watcher (tools/watch.mjs, launchd com.yetigroove.sam-portal-watch, every 10 min) renders approved rows through the HeyGen CLI on plan credits. Caps: 2 per run, 6 per day, floor 200 credits.
- Tested end to end with a 5-second row: render started, collected, row updated, 4 credits used.
- Pixabay API key saved at ~/.config/pixabay-api-key and tested (Pexels has paused new keys).
- Master Task Board updated: portal Done, 3 rows closed as superseded, 3 new rows.

**What's live / deployed:**
- samquisenberry.vercel.app (Vercel project samquisenberry, private Blob store sam-portal-rows). Key-gated, noindex. No git remote; deploys are CLI only.
- launchd job com.yetigroove.sam-portal-watch is loaded on the Mac Studio.
- Nothing sent to Sam yet. Nothing posted to Meta.

**Next up:**
- Daryl: watch ~/Archive/Clients/Sam-Insurance/renders/2026-11-20-render-test.mp4, read the 11 scripts on the admin link, then text Sam his link. Links print with: cd ~/Projects/sam-portal && . ./.env.portal && echo "https://samquisenberry.vercel.app/?k=$CLIENT_KEY"
- Still ask Sam for State Farm's footer line, his start year, and a written yes from State Farm.
- Stage 2: burned-in subtitles, Pixabay b-roll, text end card, Sam previewing the finished video, then Meta posting (blocked on his access; posting tool must set Instagram's is_ai_generated flag).

**Notes for other environments:**
- Sam's HeyGen avatar group is fb142099bdbb4843a4782c5cffa2cb93, voice 8072fb0326374b8997a2bbe945aed1b9. The group listed in YetiClone api/_clients.js is Daryl's own.
- Every tick Sam makes spends about 36 plan credits within 10 minutes if the Mac is awake. Pause with: launchctl unload ~/Library/LaunchAgents/com.yetigroove.sam-portal-watch.plist
- State Farm's agent ad rules are not public. The compliance read is a risk read, not an approval.
- AutoOwnersLogo2015Pad.jpg sits in Sam's archive folder; it is Decker's carrier logo and should move to Decker-Insurance.