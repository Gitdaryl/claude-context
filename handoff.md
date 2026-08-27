## Session: 2026-08-27 ET
**Environment:** Antigravity IDE

**What was done:**
- Overlaid this week's AI Holly reel (AUG 27-30). 8 events anchored, contrast AA, FLYTE reads TIME TBA because the feed has no time for it.
- Then automated the graphics pass so it runs with nobody at the desk.
- Four real bugs fixed: run.mjs arg() returned argv[0] for any absent flag (indexOf -1, -1+1 = 0), so --thursday was never optional; Poppins ink ran 3px past the title line box and the clamp's overflow:hidden shaved descenders, blocking the render; the SMS step checked msg.error_message but not msg.message so a 401 printed "Done."; a job-level PATH in the new workflow would have dropped setup-node's own toolchain dir.
- Date trap caught before it shipped: holly-weekend-script.js takes the UPCOMING Thursday, holly-reel-kit takes the PREVIOUS one. Identical only when run on a Thursday, seven days apart on the Wednesday cron. Job 1 now publishes the date; the overlay is told, never left to guess.

**What's live / deployed:**
- Gitdaryl/Manitou-Beach main: overlay job on a self-hosted Mac runner, chained to the render job; overlay_only dispatch input (redo graphics without re-billing HeyGen); watchdog job on GitHub hardware; named recipients on /api/internal-alert (admin default, holly from HOLLY_PHONE).
- HOLLY_PHONE added to Vercel Production, site redeployed so it binds. Endpoint verified live, auth still enforced before recipient lookup.
- Runner "yeti-mac-studio" online, labels self-hosted/macOS/ARM64, installed as a LaunchAgent.
- VERIFIED END TO END: Actions run 33099266130, all steps green. Downloaded the render from Blob, rebuilt, published to holly-weekend/overlaid/ (arms "AI Holly Post"), and correctly HELD BACK on FLYTE, texting Daryl rather than Holly.
- holly-reel-kit is now a local git repo (videos ignored, .git 1.9 MB). No remote yet.

**Next up:**
- Auto-login is OFF and the runner is a LaunchAgent, so a power cut with nobody home means the overlay queues instead of running. GitHub holds a queued self-hosted job 24h before failing.
- Push holly-reel-kit somewhere. It is load-bearing now and unbacked.
- FLYTE at Devils Lake Bar & Grill has no start time. That is what is holding this week's reel back from going to Holly automatically.
- The Holly leg of the send is unproven: every run so far held back. First clean week is the real test; a failed send falls back to texting Daryl.

**Notes for other environments:**
- Weekly manual command unchanged: nvm use 22; cd ~/Projects/holly-reel-kit/reel; node run.mjs --video=<file>. Add --deliver for the gated send, --notify to always text Daryl.
- To redo graphics on an existing take: Actions > AI Holly Weekly Video > Run workflow > overlay_only=true, week=YYYY-MM-DD. It never re-renders, so it cannot bill HeyGen twice.
- Twilio credentials exist ONLY on Vercel. Any local or CI script that texts must go through /api/internal-alert, never Twilio directly.