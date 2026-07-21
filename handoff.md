## Session: July 21, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Fixed social share previews for crowd gallery photo links on the Manitou Beach site (commit f49c543, follows yesterday's America 250 reorg cb390a3)
- Middleware now resolves /gallery/:slug?photo= against /api/photos-list and injects that photo's Blob URL as og:image, so Messenger/Facebook/iMessage cards show the actual photo instead of a bare link
- Share links from the lightbox now use the photo's stable KV id instead of its list position, so links keep pointing at the same photo as new uploads shift the feed (old numeric links still resolve by position)
- Deep-linked photos now open their lightbox even on multi-section event walls
- Verified live as facebookexternalhit: ?photo=33 on /gallery/america-250 serves the Blob photo as og:image

**What's live / deployed:**
- f49c543 pushed to main on Gitdaryl/Manitou-Beach → Vercel, verified live

**Next up:**
- Links shared BEFORE this fix (like Chelsea's) keep Facebook's cached preview; reshare the link or run it through developers.facebook.com/tools/debug to force a rescrape
- Still open from yesterday: upload America 250 photos per event via the page dropdown; paste the YouTube URL into USA250_FILM_URL when the film is live

**Notes for other environments:**
- Any crowd gallery (mens-club, ladies-club, america-250, july-4-2026) now gets per-photo share cards automatically