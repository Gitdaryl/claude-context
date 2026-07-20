## Session: July 20, 2026 (ET), part 5
**Environment:** Antigravity IDE
**What was done:**
- Ported the hardened notes API from long-shutdown-site to never-broken-site (commit c125298, deployed + promoted to production)
- Verified live on never-broken: Joe's 5 existing notes preserved; legacy notes have no tokens so nobody can delete them via UI or API (by design); new notes mint owner tokens; wrong/absent token 403s; GET leaks no tokens
- Both sites now run the identical notes stack: per-note delete tokens + post-persist NOTIFY_WEBHOOK_URL webhook (dormant until env var set)

**What's live / deployed:**
- https://never-broken-site.vercel.app (updated notes API, Joe's notes intact)
- https://long-shutdown-site.vercel.app (same stack since part 4)

**Next up:**
- Yeti: one n8n webhook URL activates note email/SMS pings on BOTH sites (add NOTIFY_WEBHOOK_URL env var to each Vercel project + redeploy; payloads carry site: never-broken / long-shutdown to route notifications)
- Everything else in ~/living-draft/SPEC.md (resolve stamps, rev changelog, greenlight meter, AI crew, visualize-this-beat) is SPEC ONLY, not built on either site
- Product next steps if pursuing: name/domain check, portfolio one-pager

**Notes for other environments:**
- The canonical hardened api/notes.js + notes.js client pattern now lives identically in both repos (Gitdaryl/never-broken-site, Gitdaryl/long-shutdown-site); copy from either
- playbook.joeprofitneverbroken.com does NOT resolve (memory was wrong or lapsed); the live URL is never-broken-site.vercel.app