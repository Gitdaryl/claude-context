## Session: 2026-06-20 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Fixed Manitou Beach bug: event organizer photos were not showing as the OG/link-preview image when event URLs were shared (Facebook, iMessage, Nextdoor).
- Root cause: MB is a client-rendered SPA; social crawlers don't run JS. The Vercel Edge Middleware (middleware.js) injected OG tags for /business/:slug pages but explicitly SKIPPED /events/:id.
- Added handleEventOG() to middleware.js (mirrors existing handleBusinessSchema): fetches /api/event-detail, injects event-specific og:image (Vercel Blob photo), og:title, og:description, twitter:* tags, and Event JSON-LD schema server-side. User text HTML-escaped; falls back to default OG on 404/unapproved/no-photo.
- Confirmed event photos are stored as permanent Vercel Blob URLs (via api/upload-image.js), NOT expiring Notion file URLs, so OG image renders reliably.

**What's live / deployed:**
- Committed to main (commit 9b44df6) and deployed to Vercel production via CLI.
- Verified live: curl as facebookexternalhit on the example event now returns the organizer's Blob photo in og:image (was returning default /images/og-image.jpg before).

**Next up:**
- None required. Fix applies to all future events automatically.

**Notes for other environments:**
- Facebook/iMessage cache previews aggressively. Already-shared links may show the old image until re-scraped. To force refresh: paste URL into Facebook Sharing Debugger (developers.facebook.com/tools/debug) → "Scrape Again". New shares pick up the photo automatically.
- Only one file changed: Manitou-Beach/middleware.js.