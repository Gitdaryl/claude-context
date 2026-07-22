## Session: July 22, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- New client Mitchel "Mitch" Ramsey onboarded (Irish Hills Realty + Devils Lake Bar & Grill); saved to memory + Session Brain
- Built and deployed the 8580 Marr Hwy listing site (900MB shoot compressed to 22MB WebP, 110 photos processed)
- Added vertical 9:16 video slot (reel-style player) for the social cut Yeti is making
- Fixed portrait photos in the gallery: letterboxed on blurred fill instead of hard-cropped, excluded from wide feature slots
- CAUGHT: drone-3 and the property-line overlay aerial have "8590 Marr Hwy" burned in; correct address is 8580 (Yeti confirmed). Both pulled from the gallery; Yeti is editing the graphics

**What's live / deployed:**
- https://irish-hills-realty.vercel.app/8580-marr-hwy (branded) and /8580-marr-hwy/unbranded (MLS-safe), verified live with 108 photos
- GitHub Gitdaryl/irish-hills-realty (private), Vercel project irish-hills-realty

**Next up:**
- Yeti edits the two 8590-captioned aerials; then recompress (full 1600px q80, thumb 420px q70 WebP), drop into public/photos/8580-marr-hwy/, restore 'drone-3' + 'drone-overlay' in the gallery list in src/data/properties.js, redeploy
- CubiCasa floorplan arrives 7/23: set floorplanImage in properties.js
- Vertical video: set videoUrl (videoAspect already 'vertical')
- Beds/baths/sqft/acreage/price from Mitch to unhide facts row
- Custom domain decision

**Notes for other environments:**
- Deploy = `cd ~/Projects/irish-hills-realty && npm run build && npx vercel deploy --prod --yes` (needs Yeti approval in IDE)
- Keep Mitch's work separate from Holly / Foundation Realty (same territory)