## Session: July 20, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Picked up the Cowork handoff for long-shutdown-site (Long Shutdown film treatment site with per-paragraph notes, same pattern as never-broken-site)
- Found the outputs folder: long-shutdown-site.zip was 0 bytes (corrupt); the real content is in long-shutdown-site-final.zip and the already-unzipped long-shutdown-site/ folder — used that
- Copied the site to ~/long-shutdown-site, git init, secret scan clean, initial commit pushed to new private repo Gitdaryl/long-shutdown-site (main, commit 591f139)
- Attempted deploy: Vercel chat connector 403s on project creation (as the handoff warned), and the CLI `vercel --prod` was blocked by this session's permission settings

**What's live / deployed:**
- Nothing yet. Repo is on GitHub; Vercel deploy still pending

**Next up:**
- Yeti runs from terminal: `cd ~/long-shutdown-site && vercel --prod --yes` (CLI is installed, logged in as yetigroove)
- Then in Vercel dashboard: Storage tab > Create Database > KV > connect to project, then `vercel --prod` again to redeploy (notes API 500s without KV)
- Verify: add a note on /treatment.html, reload, confirm it persists; have the collaborator add one too

**Notes for other environments:**
- The named zip in Cowork's outputs is corrupt (0 bytes); -final.zip is the good one. Canonical copy now lives in ~/long-shutdown-site and on GitHub (Gitdaryl/long-shutdown-site, private)
- Optional later: custom subdomain via `vercel domains add`, or connect the GitHub repo to Vercel for auto-deploy on push