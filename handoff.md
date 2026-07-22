## Session: July 22, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- New client Mitchel "Mitch" Ramsey onboarded (Irish Hills real estate + Devils Lake Bar & Grill); saved to IDE memory and Session Brain, and a "Mitch Ramsey" Project option was added to the Brain DB
- Built and shipped the listing site for his brokerage Irish Hills Realty (confirmed from yard-sign photo: office 517-467-2000, Mitch 517-403-5953)
- 900MB Dropbox shoot (114 photos) compressed to 22MB WebP; 8580 Marr Hwy page has hero, highlights, 110-photo lightbox gallery, map, agent band, sticky mobile call/text bar
- Vertical 9:16 social video slot added (renders as a centered reel); floorplan slot wired; both hidden until assets exist

**What's live / deployed:**
- https://irish-hills-realty.vercel.app deployed to production and verified. Branded: /8580-marr-hwy. MLS-safe: /8580-marr-hwy/unbranded
- GitHub: Gitdaryl/irish-hills-realty (private), Vercel project irish-hills-realty (yetigroove)

**Next up:**
- Share https://irish-hills-realty.vercel.app/8580-marr-hwy with Mitch
- CubiCasa floorplan arrives 7/23: set floorplanImage in src/data/properties.js, rebuild, redeploy
- When the vertical video is cut: set videoUrl (videoAspect already 'vertical')
- Get beds/baths/sqft/acreage/price from Mitch to unhide the facts row
- Consider a custom domain for the site or per-listing

**Notes for other environments:**
- Deploys are CLI only: `cd ~/Projects/irish-hills-realty && npm run build && npx vercel deploy --prod --yes`
- Keep Mitch's site fully separate from Holly / Foundation Realty work (same territory)