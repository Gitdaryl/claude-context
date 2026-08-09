## Session: 2026-08-09 ET
**Environment:** Antigravity IDE
**What was done:**
- Manitou Beach: built a standing auto-pin schedule for food trucks so vendors who park the same spot every week stop having to remember the check-in link
- `api/lib/autoPinSchedule.js` — config roster (slug, days, start/end ET, coords, note) + DST-correct Michigan time helpers
- `api/cron-truck-autopin.js` — posts to `/api/food-trucks` with the truck's own Checkin Token so the pin, the Departure Time auto-expiry and the Facebook/Instagram announcement fire exactly like a manual check-in; skips if the vendor already checked in (early "sold out" checkout is never overwritten); texts the vendor the pull-the-pin link after each drop
- `vercel.json` — cron `30 16,17 * * 6,0`; the ET window gate lets exactly one tick through, so 12:30 stays 12:30 across a DST flip
- `cron-truck-reminder.js` — auto-pin trucks get a heads-up instead of the "remember to check in" nag
- `HomePage.jsx` — live truck strip now respects departureTime like the food trucks page does

**What's live / deployed:**
- Pushed to main, deployed to production (manitou-beach-7lnqcnsid). Dry run on prod confirmed: fires Sat/Sun, 12:30 ET drop, 5:00 PM ET departure, truck + token resolve.
- First entry: Wieners on the Water (slug `wieners-on-the-water`), Sat + Sun, 12:30–5:00 PM ET, 41.97641336070263 / -84.28956004588389

**Next up:**
- First real auto-drop is Saturday. Watch the Vercel cron log + confirm the FB post fires.
- Not built: a "skip today" toggle (bad weather / day off). Right now the vendor pulls the pin after it drops, one tap from the SMS. Would need a new Notion column or a KV flag.

**Notes for other environments:**
- Adding another truck to the schedule is a one-line edit in `api/lib/autoPinSchedule.js` + deploy.
- Test without side effects: `GET /api/cron-truck-autopin?dryRun=1` with `X-Admin-Token: $ADMIN_SECRET`. Add `force=1` to bypass the day/time gate (this one really posts to Facebook and texts the vendor).
- Local `.env` NOTION_TOKEN_BUSINESS is stale/401 — query prod endpoints instead of Notion directly from the laptop.