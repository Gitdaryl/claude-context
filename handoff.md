## Session: 2026-08-17 ET
**Environment:** Antigravity IDE

**What was done:**
- Rebuilt the Sunny Skies posting dispatcher for Isaac's new approval workflow (he drops approved videos in Drive `Approval Folder/READY`, previously a category-pool system)
- Reused the existing paused VPS rig rather than building anything new: `root@143.198.171.9:/root/SunnySkies/`
- New two-tier design: Tier 1 MOVES the oldest video from READY into a new POST QUEUE folder (so READY drains and the count is a real runway gauge); Tier 2 falls back to the old evergreen category pools when READY is dry, so posting never goes silent
- Schedule changed to 5/day at 8am, 10am, 12pm, 2pm, 4pm ET, per Isaac's request
- Made the schedule DST-proof: cron now fires hourly and `dispatcher.js auto` resolves the real Eastern hour itself. Debian cron 3.0pl1 on this box ignores both `TZ` and `CRON_TZ`, so fixed UTC times would have slipped an hour on Nov 1
- Added refill notifications: SMS to Yeti (`+15172605907`) via Twilio, email via Resend, fires at 10/5/2/0 remaining, deduped so it does not text 5x a day. Isaac is registered but OFF pending his channel choice
- Long-form guard: anything over 150MB in READY is skipped and logged, not posted as a Reel
- Added `status.js` and `set-recipient.js` operator scripts, plus `RUNBOOK-dispatcher.md`

**Bugs found and fixed along the way:**
- The Vercel admin UI was never actually connected. `config-server.js` requires a bearer token and 401s without it, but `dispatcher.js` sent no auth header, so every config fetch silently returned null. The pause toggle and timetable had done nothing for months; only `tracking.json` ever paused it
- `RESEND_API_KEY` was never set on the VPS and the failure handler was `if (!key) return;`, so every dispatcher failure since launch was silent
- Config server now MERGES posts instead of overwriting, because the stale admin UI would otherwise wipe the new notify block on every save

**What's live / deployed:**
- New dispatcher, config server and hourly crontab deployed to the VPS. Dated backups of every file sit alongside
- New Drive folder POST QUEUE: `1BR8_kcQNUVXJR5uFY58C8fZPPlGJBIub`
- Twilio + Resend credentials copied from Manitou-Beach `.env.local` to `/root/SunnySkies/.env`
- Test SMS sent and confirmed received by Yeti
- **STILL PAUSED on purpose.** Nothing posts until Repurpose is rewired

**Next up:**
1. Point one Repurpose.io workflow at POST QUEUE (`1BR8_kcQNUVXJR5uFY58C8fZPPlGJBIub`), then `./resume.sh` and clear paused in the admin UI
2. Ask Isaac SMS or email, then `node set-recipient.js Isaac --sms ...` or `--email ...`
3. Decide on `Priscilla Dan Full build.mp4` (319MB, currently skipped) — likely belongs in the existing `Long form for YT` folder
4. Runway is thin: 13 postable videos at 5/day is ~2.6 days. The evergreen fallback covers the gap but Isaac needs to feed steadily
5. Admin UI timetable is stale (still 9am/12pm/6pm) and now only governs the fallback tier

**Notes for other environments:**
- Runbook lives at `Documents/Claude Code/Sunny-Skies/RUNBOOK-dispatcher.md`, source mirrored to `Sunny-Skies/dispatcher/`
- Repo is not a git repo, so nothing was pushed