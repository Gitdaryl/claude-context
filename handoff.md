## Session: July 22, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Onboarded new client Mitchel "Mitch" Ramsey: Irish Hills real estate + Devils Lake Bar & Grill. Saved to IDE memory + Session Brain (new "Mitch Ramsey" Project option added to the Notion DB)
- Discovered from the shoot photos that Mitch's brokerage is Irish Hills Realty (office 517-467-2000, cell 517-403-5953)
- Downloaded the 900MB Dropbox shoot (114 photos), compressed to 22MB of WebP (full 1600px + 420px thumbs)
- Built the listing site: repo ~/Projects/irish-hills-realty, pushed to GitHub Gitdaryl/irish-hills-realty (private). Vite + React, editorial cream/pine/wheat design, Fraunces type
- 8580 Marr Hwy page: hero, highlights, 110-photo grid with lightbox, Google Map embed, agent band, sticky mobile call/text bar, plus /unbranded MLS-safe route
- Video and CubiCasa floorplan slots are wired but hidden (nulls in src/data/properties.js); beds/baths/sqft/price also null and hidden until Mitch confirms
- Verified with local Playwright screenshots (desktop + mobile)

**What's live / deployed:**
- GitHub repo pushed. NOT yet deployed to Vercel: the production deploy command was blocked by the permission classifier; Yeti needs to run/approve `npx vercel deploy --prod --yes` in ~/Projects/irish-hills-realty

**Next up:**
- Deploy to Vercel (command above), then verify live and share URL with Mitch
- Tomorrow: CubiCasa floorplan arrives; set floorplanImage in src/data/properties.js
- Property video still to be produced; set videoUrl when ready
- Get beds/baths/sqft/acreage/price from Mitch to fill the facts row
- Consider a custom domain (e.g. 8580marrhwy.com or irishhillsrealty listing subdomain)

**Notes for other environments:**
- Mitch's listing photos original files remain in Dropbox; compressed WebP set lives in the repo
- Holly (Foundation Realty) and Mitch both work the Irish Hills area; keep the two clients' branding and site work separate