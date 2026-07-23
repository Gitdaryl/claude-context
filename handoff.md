## Session: July 23, 2026 ET (IDE, Mitch Ramsey listing site)
**Environment:** Antigravity IDE

**⚡ FIRST THING NEXT DESKTOP SESSION (Yeti asked to be reminded):**
```
cd ~/Projects/irish-hills-realty && npx vercel env add RESEND_API_KEY production
# paste the Resend key (same as Holly project), then:
npx vercel deploy --prod --yes
```
Optionally also `npx vercel env add LEAD_EMAIL production` with Mitch's email (defaults to admin@yetigroove.com). This turns on instant email alerts for showing requests; leads are already persisting safely without it.

**What was done today:**
- CubiCasa floor plans live + enlargeable (tap-to-zoom with pan); facts corrected to 3,778 finished sqft
- Around the Area section: OSRM driving distances from drone-EXIF GPS
- Three-POV review implemented: Coming Soon badge, gallery jump chips, Vercel Analytics, EHO/disclaimer footer, JSON-LD
- Save hearts + view counters (public only past 100 views / 5 saves); Blob event-counter pattern after catching CDN-cache increment loss
- Request-a-Showing form: persist-before-notify verified live; key-protected /api/leads (key: Desktop/irish-hills-leads-key.txt); one TEST lead in store

**What's live / deployed:**
- https://irish-hills-realty.vercel.app/8580-marr-hwy everything above, verified

**Next up (after the Resend command):**
- Mitch: list price (flip status to For Sale), MLS photo cap (then I cut the 2048px export), well/septic/heat/internet/school facts for a Good to Know section
- Print flyer + QR, custom domain decision, vertical video, FB debugger priming

**Notes for other environments:**
- Full detail in Session Brain rows July 22-23, Project: Mitch Ramsey
- Mobile: listing URL to share with Mitch is https://irish-hills-realty.vercel.app/8580-marr-hwy