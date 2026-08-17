## Session: 2026-08-17 ET
**Environment:** Antigravity IDE

**What was done:**
- Rebuilt the Sunny Skies posting dispatcher for Isaac's new approval workflow (he drops approved videos in Drive `Approval Folder/READY`, replacing the old category-pool system)
- Reused the existing paused VPS rig rather than building anything new: `root@143.198.171.9:/root/SunnySkies/`
- Tier 1 MOVES the oldest video from READY into a new POST QUEUE folder, so READY drains and its count is a real runway gauge
- A Tier 2 fallback to the old evergreen pools (counted: 315 videos across 16 folders) was built and tested, then **deliberately disabled** at Yeti's call: those pools predate Isaac's approval workflow, so auto-posting them risks publishing content the client never approved. When READY is empty, posting stops and Yeti gets one text a day. Re-arm with `fallbackEnabled: true`
- While counting the pools, found `urgency` empty (0 videos) and `investment` returning no access. Under the old code either would have killed the whole slot on days 4/9/14/19/24/29 of the month. Fallback now tries every other pool before giving up, fixed even though the feature is off
- Schedule set to **4/day at 8am, 11am, 2pm, 5pm ET**. Isaac asked for 5/day; Yeti chose 4 to stretch the runway about half a day
- Made it DST-proof: cron fires hourly and `dispatcher.js auto` resolves the real Eastern hour itself. Debian cron 3.0pl1 on this box ignores both `TZ` and `CRON_TZ`, so fixed UTC times would have slipped an hour on Nov 1
- Refill notifications: SMS to Yeti (`+15172605907`) via Twilio, email via Resend, firing at 10/5/2/0 remaining, deduped per level. Empty-folder alerts are once per day, not once per slot. Isaac deliberately left OFF: Yeti relays personally rather than auto-nagging a disengaged client
- Long form auto-routed: anything over 150MB moves from READY into the existing `Long form for YT` folder with one alert. Moved `Priscilla Dan Full build.mp4` (319MB) there; that folder already held two full roof replacement ASMR videos
- Added `status.js` and `set-recipient.js` operator scripts plus `RUNBOOK-dispatcher.md`
- Drafted a short client email to Isaac (deliberately no questions in it, so it needs no reply)

**Bugs found and fixed along the way:**
- The Vercel admin UI was never actually connected. `config-server.js` requires a bearer token and 401s without it, but `dispatcher.js` sent no auth header, so every config fetch silently returned null. The pause toggle and timetable had done nothing for months; only `tracking.json` ever paused it
- `RESEND_API_KEY` was never set on the VPS and the failure handler was `if (!key) return;`, so every dispatcher failure since launch was silent
- Config server now MERGES posts instead of overwriting, because the stale admin UI would otherwise wipe the notify block on every save

**What's live / deployed:**
- New dispatcher, config server and hourly crontab on the VPS, with dated backups of every file. VPS and local mirror verified identical by checksum
- New Drive folder POST QUEUE: `1BR8_kcQNUVXJR5uFY58C8fZPPlGJBIub`
- Twilio + Resend credentials copied from Manitou-Beach `.env.local` to `/root/SunnySkies/.env`
- Test SMS sent and confirmed received by Yeti
- Current state: 13 postable in READY, ~3.3 days of runway, fallback OFF
- **STILL PAUSED on purpose.** Nothing posts until Repurpose is rewired

**Next up:**
1. Point one Repurpose.io workflow at POST QUEUE (`1BR8_kcQNUVXJR5uFY58C8fZPPlGJBIub`), then `./resume.sh` and clear paused in the admin UI (both switches must be off)
2. Send Isaac the email, ideally after going live
3. With the fallback off, the accounts go dark if Isaac lags. Watch the first dry spell to see whether that pressure works or whether the fallback needs re-arming
4. Decide whether `Long form for YT` should get its own Repurpose workflow for real YouTube publishing; right now it is staging only
5. Admin UI timetable is stale (still 9am/12pm/6pm) and now only governs the disabled fallback tier

**Notes for other environments:**
- Runbook at `Documents/Claude Code/Sunny-Skies/RUNBOOK-dispatcher.md`, source mirrored to `Sunny-Skies/dispatcher/`
- Not a git repo, so nothing was pushed