## Session: 2026-05-30 AEST
**Environment:** Antigravity IDE
**What was done:**

- COO audit led to focused Sunny Skies dispatcher overhaul
- Identified root cause of rotation bug: old routines sorted by `createdTime ascending` so same clips always fired first
- Built `clip-index.json` in `Sunny-Skies/sunny skies stills/10 sec library/` — 46 clips indexed with mood/subject/category tags, 14 flagged review_needed
- Saved clip library memory file + MEMORY.md pointer
- Created 4 new RemoteTrigger routines (all ENABLED):
  - `trig_014nEu4EaMg2L9M78YhRRgoP` — Quotes 9am ET, sorts by last_posted ASC
  - `trig_01SPThcf6gzLaqZiWvohqaFh` — Midday 12pm ET, sorts by last_posted ASC
  - `trig_01GHbiikKb2FimTsCXPVuEPc` — Evening 6pm ET, sorts by last_posted ASC
  - `trig_011qiFPmvXTmbSoxzDiMUvNN` — Fuel Gauge 9:10am ET, Haiku model, checks all 16 Drive folders, SMS alert when any hits ≤7 days
- Disabled all 3 old/broken routines (trig_01Lrty15t44wKwZDT3DaKthC, trig_011kXD1oFtWQx3CMJ5GMuDnQ, trig_01NnLEi2N4zTE1RJ2nTUmwPG)
- Added `api/fuel-alert.js` and `api/internal-alert.js` to Manitou Beach — SMS endpoints for automation
- Committed, pushed, and deployed MB to Vercel production
- FUEL_ALERT_TOKEN (`fgss2026xpk7`) and ADMIN_PHONE (`+15172605907`) confirmed live in Vercel env

**What's live / deployed:**
- manitoubeachmichigan.com/api/fuel-alert — live, used by fuel gauge routine
- manitoubeachmichigan.com/api/internal-alert — live, general-purpose ops alerts
- All 4 new dispatcher routines active and will fire from tomorrow morning

**Next up:**
- Review 14 flagged clips (Install 1-7, rooftop 1-5, shingles 1) — watch them, update clip-index.json entries
- Fix filename typos: `flu up 1.mov` → `fly up 1.mov`, `timplapse build.mov` → `timelapse build.mov`
- Upload local 10 sec library to Google Drive `dyoung@callsunnyskies.com` under `_dispatcher/video-bg-library/` (currently local only)
- Clean up TEST trigger `trig_01LEkWL8pRFypYuYHnyKQqTU` (disabled but exists)
- MCP redundancy cleanup: 4 Notion MCPs, 2 Vercel MCPs — prune duplicates
- Install missing CLIs: stripe, yt-dlp, pnpm, Playwright

**Notes for other environments:**
- Dispatcher is now on new routines — old ones are OFF. Do not re-enable them.
- Fuel gauge SMS token is `fgss2026xpk7` (stored as FUEL_ALERT_TOKEN in Vercel)
- clip-index.json is local only — needs Google Drive upload before mobile can use it