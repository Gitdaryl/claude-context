## Session: 2026-08-27 ET
**Environment:** Antigravity IDE

**What was done:**
- Overlaid the AI Holly reel for AUG 27-30, automated the whole graphics pass, then did a full redo when Cherry Creek Cellars landed three listings in their first week.
- AUTOMATION: a second job on the Wednesday workflow runs the overlay on the Mac Studio through a self-hosted GitHub runner, chained to the render job. Added overlay_only (redo graphics without re-billing HeyGen) and a watchdog job on GitHub hardware, because the overlay's own failure alert runs on the Mac and cannot fire when the Mac is the problem. The watchdog earned its keep the same day.
- SEND: routed off Twilio (which had credentials nowhere) onto the site's /api/internal-alert with named recipients. Gated: Holly only gets a clean reel, otherwise Daryl gets it with the reason.
- SCRIPT: strict chronological order, the AI-jealousy aside freed from the opener onto any distinctive event, "in the evening" for a missing time, and she no longer reads street addresses.
- GRAPHICS: spine tapers to a faded point, cards end on Holly's own pause with bare video between topics, closing URL card, colour-bearing logos fill the circle (measured via ffmpeg), whooshes on card in and out.

**What's live / deployed:**
- THE REEL WENT TO HOLLY AUTOMATICALLY at the end of the session: run 33109490254 logged "delivering / texted holly / texted admin". First time the Holly leg has actually fired.
- Master published to holly-weekend/overlaid/, which arms "AI Holly Post". Nothing posted to Facebook or Instagram yet.
- 11 events, chronological, Cherry Creek on three cards with their own logo filling the circle.
- Runner yeti-mac-studio online. HOLLY_PHONE on Vercel Production. holly-reel-kit under local git, still no remote.

**Next up:**
- Post it: Actions > "AI Holly Post". That path has still never published to Meta.
- Ask Cherry Creek when someone answers: Friday says 6-10 and Saturday 6-9, probably a typo; and their description says music 7-10 while the listing starts at 6, so "doors at 6" may be truer for future weeks.
- Mac auto-login is still off, so a power cut with nobody home queues the Wednesday job.
- Push holly-reel-kit somewhere.

**Notes for other environments:**
- Redo graphics with no HeyGen charge: Actions > AI Holly Weekly Video > Run workflow > overlay_only=true, week=YYYY-MM-DD.
- Twilio credentials exist ONLY on Vercel. Anything that texts must go via /api/internal-alert.
- Events DB traps: dateEnd is sometimes a season end, not an event end. Time is a read-only created_time field and real times live in Time End split on an EN DASH; a single time in there is read as the START.