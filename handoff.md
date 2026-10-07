
## Session: 2026-10-07 (ET)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD home page: Jay, Devon, Kyle, Linda headshots replace the initial circles in the Family section (assets/photos/team-*.webp, 192px, cropped inside the baked-in circle). Verified by headless screenshot.
- WebP sweep converted 3 images (1.3 MB -> 0.6 MB). brand/cleanup (89 MB scratch) added to .gitignore.
- Committed and pushed everything to Gitdaryl/on-point-jd master (15fe45d): headshots + the $1,000 /estimate offer + bonus wheel + /desk back end that had been sitting uncommitted since Oct 5.

**What's live / deployed:**
- Nothing new. Push does not trigger Vercel for this project (last deploy 4 days old). The CLI production deploy was blocked by permissions. Yeti runs:  cd ~/Projects/on-point-jd/site && vercel --prod --yes

**Next up:**
- Deploy (above). After deploy, confirm https://onpointjd.com/assets/photos/team-jay.webp returns image/webp.
- Deploying makes the $1,000 offer active on /estimate by default (active:true, 60s dwell, ends Oct 31, ZIPs 434/435/436). /estimate is noindex and unlinked, but Jay/Devon have NOT approved the bonus list (CONFIRM.md). To hold it: set OFFER_DESK_PIN in Vercel and flip active off at /desk, or set active:false in api/lib/offer.js DEFAULTS before deploying.
- OFFER_DESK_PIN env var is not set in Vercel, so /desk is locked out until it is.

**Notes for other environments:**
- Source headshot PNGs are in Desktop/onpoint assets (Devon, Jay, Linda, kyle).