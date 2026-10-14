## Session: Oct 14 2026 (afternoon ET)
**Environment:** Antigravity IDE
**What was done:**
- Tore down Contractor Liberty's lead-gen funnel (go.contractorliberty.co): Meta ad -> GoHighLevel page -> roasform quiz above the fold with a revenue gate -> pay-per-sit appointments; their real product is a human qualifying call within minutes. Screenshots in the session scratchpad.
- Decided the OnPoint ad pilot model: Yeti fronts Meta spend (cap $1,500/mo), 10% of contract value per attributed closed job, attribution by OnPoint Office, 90-day pilot from ~March 2027. Plan written to on-point-jd/social/ADS-PILOT.md (deal, funnel parts, first campaign, kill/scale rules, template for other trades). Memory: onpoint-ad-pilot-pay-per-job.md.
- PRE-WIRED the Meta pixel + Conversions API in both repos, all gated on META_PIXEL_ID + META_CAPI_TOKEN (nothing fires until set):
  - on-point-jd/site: api/lib/meta.js (CAPI client, hashing), api/pixel.js (env-gated pixel script loaded by site.js on every page), site.js (fbclid/_fbp/_fbc capture, Lead + Contact browser events with shared event ids), api/lead.js (server Lead), api/track.js (server Contact). tools/test_meta.mjs (5 tests) + existing 37 pass. stamp_assets.py re-run (21 html files changed by hash only).
  - onpoint-office: api/_lib/meta.ts (pure planner + sender), api/meta-sync.ts (hourly cron, Lead/Schedule/Purchase once each), supabase/migrations/20261102000000_meta_events.sql (server-only table + job_runs allows 'meta-sync'), vercel.json cron 17 * * * *, env.ts getters, docs/SERVER.md rows, tests/meta.logic.test.ts (9 tests). tsc + oxlint clean; handler smoke-tested (401/405/503 paths).
- Board: new Decision row "first Meta ad spend ... DECIDE funding model"; "Meta access for Daryl" row updated with the exact next clicks.

**What's live / deployed:**
- Nothing deployed. Both repos have uncommitted changes (office also carries another session's uncommitted work in src/lib/jobs etc.; do not reset). Migration NOT pushed to live Supabase.

**Next up:**
- Yeti: Meta business portfolio > ad account > dataset (Pixel ID) > CAPI token > domain verify > `vercel env add` on both projects > redeploy > Events Manager Test events.
- Commit + push both repos when Yeti says so (commit-push skill); `supabase db push` for meta_events with the 3 pending migrations.
- Ads-only Twilio number, lead alerts + text-back deploy, persona pages, 5-reel creative bank (ADS-PILOT.md parts 3 to 7).

**Notes for other environments:**
- Winter spend is $10/day storm/ice-dam creative to warm the pixel only; replacement ads judged from March 2027.
- Ask Jay in person: what Devon earns per sale, and settle the agreement row before any commission addendum.