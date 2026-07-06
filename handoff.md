## Session: 2026-07-06 ET
**Environment:** Antigravity IDE

**What was done:**
- Built a CrowdReel-style community photo feature for the Manitou Beach site (scan a QR board at an event → upload photos → live public gallery). Bolted onto the EXISTING gallery system rather than a new app.
- New API: api/photos-upload, photos-list, photos-report, photos-admin + api/lib/photos.js (Upstash Redis store) + api/lib/photo-slugs.js (server allowlist).
- New UI: src/components/EventPhotoWall.jsx (drop-in module: upload + live feed + flag), src/pages/GalleryHubPage.jsx (/gallery index), src/pages/GalleryAdminPage.jsx (/gallery-admin mobile takedown + printable QR board).
- Extended src/data/galleries.js (crowd galleries: america-250, ladies-club, july-4-2026), GalleryPage.jsx (merges crowd feed + module), PhotoGallery.jsx (added thumbOf + onReport props), App.jsx routes, middleware.js OG mirror.
- Live feed model per Yeti's call: photos post instantly; community can flag; 3 flags auto-hides; Yeti has one-tap takedown. Images downscaled in-browser (max 1600px) before upload; Claude-Vision SEO filenames; stored in Vercel Blob.

**What's live / deployed:**
- Pushed to main (commit 72ab09c), Vercel auto-deploying manitoubeachmichigan.com.
- Code is live but the photo store is INERT until the one setup step below is done (endpoints no-op gracefully, existing site unaffected).

**Next up (Yeti's one setup step):**
- Vercel dashboard → Storage → Marketplace → add Upstash Redis → connect to the `manitou-beach` project. That injects the REST env vars and the whole feature switches on. Phone-friendly, ~4 taps.
- Set ADMIN_SECRET env var (if not already) — it gates /gallery-admin (reuses existing pattern).
- To attach the photo wall directly onto a specific event page (e.g. USA250Page or LadiesClubPage), tell the IDE: it's a one-liner `<EventPhotoWall slug="..." title="..." />`.

**Notes for other environments:**
- Metadata store is Upstash Redis (NOT legacy Vercel KV — that's deprecated). Helper reads KV_REST_API_* or UPSTASH_REDIS_REST_* env names.
- Crowd galleries live in TWO places that must stay in sync: src/data/galleries.js (crowd:true) and api/lib/photo-slugs.js (server allowlist). Add a slug to both.
- Public gallery URL: /gallery/<slug>. Hub: /gallery. Admin: /gallery-admin.