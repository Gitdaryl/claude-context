## Session: 2026-07-06 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Reviewed Yetickets + Manitou Beach from user / event-organiser / admin points of view; found and fixed a batch of real bugs across both.
- Manitou food trucks (the big one): fixed why the "truck is open today" auto-post never fired — the code read env names META_* but production uses FB_*/IG_*; added the fallback so it now finds the token. Added a peak-season reminder cron (texts active trucks their pin-drop link, weekends 10am ET, May–Sep). Made the auto-post alert by SMS on failure instead of failing silently. Fixed a site-wide security header that was silently blocking the GPS pin-drop. Removed an old instant-publish endpoint that bypassed moderation. Fixed event-date bugs (events vanishing early / on time-of-day). Rewrote README to the real workflow and flagged the dead monolith file.
- Yetickets: hardened the Stripe webhook (idempotent, persists+retries, awaits confirmation emails, maxDuration). Fixed an org data-leak (dashboard filter contains→equals) and added a duplicate-org-name guard. NOTE: another environment had hardened the same webhook in parallel; merged both, keeping their payment_status gate + sponsor idempotency plus my awaited-emails + maxDuration.
- Vercel: marked plaintext secrets as Sensitive; set a fresh CRON_SECRET (the old one was flagged "Needs Attention").
- Removed hardcoded Notion tokens from a one-off migration script (now reads from env).

**What's live / deployed:**
- Manitou-Beach `main` @ 75f6d8c — pushed, Vercel auto-deployed. Home + /api/food-trucks return 200.
- Yetickets `master` @ 639dbc8 (merge commit) — pushed, Vercel auto-deployed. Home returns 200.

**Next up:**
- Notion token rotation: DEFERRED on purpose. The exposed tokens never left the local machine (never committed to git; Documents is not cloud-synced), so exposure is contained and low-risk. Rotating live tokens risks site downtime and is now awkward (tokens are Sensitive-masked in Vercel). Do it later only as a deliberate, one-token-at-a-time mini-deploy if wanted.
- Verify the food-truck auto-post on the next real check-in (should post to FB/IG now; a failure will text the admin).
- Reminder cron first fires this Saturday 10am ET.
- Nice-to-haves discussed: manual map-tap fallback for the pin-drop, /api/health endpoints on both apps, and the coupon/attribution loop (post link already carries ?ref= tags for it).

**Notes for other environments:**
- Yetickets stripe-webhook.js was edited in TWO places at once this session (IDE + another env). Now merged. Pull before touching it again.
- Social-posting code reads BOTH META_* and FB_*/IG_* env names; production is configured with FB_*/IG_*.