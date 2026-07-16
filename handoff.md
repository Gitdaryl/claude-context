## Session: 2026-07-15 (night ET)
**Environment:** Antigravity IDE
**What was done:**
- Added paragraph notes to the Never Broken treatment page so Joe can comment inline: "add note" under every paragraph, notes render as sticky notes matching the binder aesthetic, name remembered per device, anyone with the link can add/delete (no auth by design, link-only site)
- Backend: Vercel Blob store `never-broken-notes` created and linked to the project; api/notes.js (GET/POST/DELETE) with persist-first logging; api/health.js self-check per build standard
- All 29 content paragraphs got stable data-nb ids (rule: never renumber, notes are keyed to them)
- Version workflow set up: "Draft v1" chip + date in header; from v2 on, changed paragraphs get class="revised" data-rev="v2" (gold left border + tag), cleared next version. No word-level track-changes colors. Full workflow in repo README.md
- Tested locally (vercel dev + Playwright UI drive), deployed, verified production: health ok, notes API live, UI screenshot confirmed

**What's live / deployed:**
- https://never-broken-site.vercel.app/treatment.html with working notes
- https://never-broken-site.vercel.app/api/health self-check

**Next up:**
- Send Joe the link, tell him to tap "add note"
- When revising: follow README version workflow (bump chip, mark revised paragraphs, git tag)
- Optional: subdomain playbook.joeprofitneverbroken.com

**Notes for other environments:**
- Notes live in Vercel Blob store never-broken-notes (own store, nothing borrowed from manitou-beach)
- Repo: Gitdaryl/never-broken-site, auto-deploys on push to main