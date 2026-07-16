## Session: 2026-07-15 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Picked up HANDOFF-never-broken-site.md from Downloads (built earlier today in claude.ai chat)
- Moved unzipped site from ~/Downloads/never-broken-site to ~/never-broken-site
- Git repo initialized, pushed to private repo github.com/Gitdaryl/never-broken-site
- Deployed to Vercel (project: never-broken-site, scope: yetigroove)
- Verified live: index + treatment return 200, noindex meta present on both pages, robots.txt blocking all crawlers

**What's live / deployed:**
- https://never-broken-site.vercel.app (playbook at /, treatment at /treatment.html) — link-only, not indexed. This is the link to send Joe.

**Next up:**
- Optional: attach playbook.joeprofitneverbroken.com subdomain in Vercel dashboard (Settings → Domains on the never-broken-site project)
- Send Joe the link

**Notes for other environments:**
- claude.ai Vercel connector was failing (empty team list); IDE's Vercel CLI auth worked fine, used that
- Site is NOT connected to GitHub auto-deploy; redeploys are manual via `vercel` in ~/never-broken-site