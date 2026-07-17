## Session: July 16, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Picked up Spotted Owl Event Co. site from Cowork's HANDOFF.md (Cowork outputs folder)
- Moved repo to permanent home: `~/Projects/spotted-owl-site/` (original copy + zip still in Cowork outputs)
- SEO pass: added meta description, OG tags, and an inline SVG owl favicon (brass-on-ink, matches brand)
- git init, initial commit, created private GitHub repo `Gitdaryl/spotted-owl-site`, pushed main
- Deployed to Vercel production via CLI: https://spotted-owl-site.vercel.app
- Connected Vercel project to the GitHub repo, so pushes to main now auto-deploy
- Verified live site with headless Chromium screenshot: hero, candles, nav, CTAs all render

**What's live / deployed:**
- https://spotted-owl-site.vercel.app (production, Vercel project `spotted-owl-site` under yetigroove account)
- https://github.com/Gitdaryl/spotted-owl-site (private)

**Next up:**
- Wire the inquiry form (Formspree or serverless -> email). Blocked on: confirm destination inbox with Yeti (admin@yetigroove.com assumed). Remember build standard: persist order/lead before notifying + /api/health.
- Swap placeholder media as real photos arrive (wizard party, wands, owl post, castle mural, dessert tables)
- Real Instagram/Etsy URLs in footer (currently `#` stubs)
- og:image once a real hero photo exists
- Custom domain (spottedowlevent.co / spottedowleventco.com — not yet checked or purchased)

**Notes for other environments:**
- Repo root is now `~/Projects/spotted-owl-site/` — do NOT edit the copy in Cowork outputs anymore
- HANDOFF.md is gitignored and stays local only
- IP rule still applies: generic theme names only, never franchise names/logos/fonts