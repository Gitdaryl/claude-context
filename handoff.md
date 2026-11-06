## Session: 2026-11-06 ET
**Environment:** Antigravity IDE
**What was done:**
- Moved all scheduled MB posts and the Nov 20 hero switch off the Claude session onto a Mac launchd job.
- Dry-ran all 7 rows, ran the job through launchd, sandbox-tested good post, rerun, failure and missed day.
- Removed the 7 session-only jobs.

**What's live / deployed:**
- com.yetigroove.mb-daily-post installed. First real post: Faust House, Sun Nov 8, 11:17 AM ET.

**Next up:**
- Build float reels Nov 19 and Nov 23, then add them to rotation/schedule.json.
- Read rotation/post-log.json each session. Look at the home page Nov 20.

**Notes for other environments:**
- Claude sessions can close now. The Mac has to stay on. Runbook: rotation/SCHEDULE-JOBS.md.