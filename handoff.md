## Session: 2026-08-31 (ET)
**Environment:** Antigravity IDE
**Project:** Manitou Beach (Gitdaryl/Manitou-Beach)

**What was done:**
- Built the poster QR router: printed A-frames encode only `/snap/<key>`, never a deep
  link, so one board works for every event an org runs and routing stays changeable
  without a reprint. `/api/snap-resolve` reads the live events feed at scan time and
  pre-picks the event; the page shows the pick as a confirmable chip, never silently.
  Covers morning-after uploads, two-events-at-once, cancelled events, weekly recurring
  venues, and a Notion outage (returns 200, not 503).
- Designed and generated the 24x36 Men's Club poster. Print-ready vector PDF with
  0.125in bleed, "SHARE YOUR SHOTS", 12.2in QR at error correction Q. Verified by
  decoding the QR back out of the rendered artwork.
- Priced crowd photo galleries against live Vercel/Upstash rates: ~$10/yr per venue,
  almost all of it the Haiku vision pre-screen. Decision: charge for moderation and
  setup as a flat annual add-on, never metered storage. Clubs stay included as the demo.
- Filed the Men's Club Golf Outing (Sep 13 2026) in Notion and made it the home page
  hero with a Learn More CTA to /mens-club.
- Fixed two hero bugs found on the way: `Time` is a created_time system field so every
  featured event rendered with no time, and an event with both a background and an
  inline image rendered the same subject twice, pushing the CTA to the fold edge.

**What's live / deployed:**
- manitoubeachmichigan.com/snap/mensclub (verified 200, resolver + page render)
- Home page hero is now the Golf Outing with video background and CTA to /mens-club
- marketing/posters/mensclub-poster.pdf, regenerate with `node scripts/make-poster.mjs <key>`
- Pushed through commit fce7a75

**Next up:**
- Print two copies of the poster for the A-frame (front and back, same design)
- Purge is unbuilt: admin can hide a photo but not delete it. Needed before selling a
  gallery to a paying venue.
- Each new venue gallery is currently a code deploy across three files. Should become
  one config entry if this becomes a product.
- Logo art reads "DEVIL'S & ROUND LAKE"; canonical name everywhere else is
  "Devils Lake & Round Lake Men's Club". Worth checking with the club before print.

**Notes for other environments:**
- Notion events DB gained a `Tagline` rich_text property (api/hero.js already read it
  but it did not exist, so hero taglines were always blank).
- `Cost` must always be set explicitly on an event; blank publishes as free.