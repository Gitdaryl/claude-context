## Session: July 20, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Picked up the Cowork handoff for long-shutdown-site (Long Shutdown film treatment site with per-paragraph notes)
- The named zip was 0 bytes (corrupt); used the good copy from long-shutdown-site-final.zip / the unzipped folder
- Site moved to ~/long-shutdown-site, pushed to private repo Gitdaryl/long-shutdown-site
- Cowork's build used Vercel KV (dashboard-only setup); swapped the notes API to Vercel Blob, porting never-broken-site's proven api/notes.js, so the whole thing could ship from CLI with zero manual steps (commit a7ddb1a)
- Created blob store long-shutdown-blob, linked it to the project (expect script to drive the CLI prompts), deployed, redeployed to pick up the env var
- Verified end-to-end with curl: GET/POST/DELETE on /api/notes all work, note persisted across requests, test notes cleaned up

**What's live / deployed:**
- https://long-shutdown-site.vercel.app (production, noindex + robots blocked, link-only)
- Treatment at /treatment.html with working per-paragraph notes backed by Vercel Blob

**Next up:**
- Nothing required. Optional: custom subdomain (`vercel domains add` or dashboard), connect GitHub repo for auto-deploy on push
- Optional cleanup: three empty leftover blob stores from CLI prompt fighting (ls-notes, ls-notes-2, long-shutdown-notes) can be deleted in dashboard Storage tab; they're free and harmless

**Notes for other environments:**
- IMPORTANT for Cowork: when generating notes-widget sites for CLI deploy, use @vercel/blob (never-broken pattern), NOT @vercel/kv. KV can only be attached via dashboard; Blob works entirely from CLI. This is why never-broken shipped hands-free and this one initially needed manual steps
- Redeploys are manual: `vercel redeploy https://long-shutdown-site.vercel.app` or `vercel deploy` from ~/long-shutdown-site