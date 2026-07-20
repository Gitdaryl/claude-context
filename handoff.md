## Session: July 20, 2026 (ET), part 4
**Environment:** Antigravity IDE
**What was done:**
- Closed both collaboration gaps on long-shutdown-site (commit 6c4024f, live in production):
  1. Per-note delete tokens: POST mints a secret only the author's browser keeps (localStorage nb-tokens), GET strips it, DELETE requires it. Verified live: foreign/absent token 403s, owner delete works, delete button only renders on your own notes
  2. Post-persist notify webhook: set NOTIFY_WEBHOOK_URL env var on the Vercel project and every new note POSTs JSON (event, site, para, name, text, ts, url) to it AFTER the blob write succeeds (persist-before-notify standard). Wire to n8n for email/SMS pings; no code change needed to activate
- Wrote the product spec for the templatable offering: ~/living-draft/SPEC.md ("Living Draft" working name). Producer/writer persona: momentum mechanics (note pings, read receipts, resolve stamps, rev changelogs, greenlight meter of locked stamps, decision log), AI crew inside (script doctor citing Vogler/McKee/Snyder for gap-finding, instant coverage, comp finder, visualize-this-beat image gen with character continuity, table read TTS, pitch pack export), zero-login guests as the moat, roadmap v0 hand-built -> v0.5 productized service (5 paying projects) -> v1 SaaS

**What's live / deployed:**
- https://long-shutdown-site.vercel.app with note ownership + webhook hook in production

**Next up:**
- Yeti: provide an n8n webhook URL to activate note email/SMS pings (I add NOTIFY_WEBHOOK_URL to Vercel env and redeploy)
- If pursuing the product: name/domain check, then the portfolio one-pager
- never-broken-site still has the old notes API (no tokens, no webhook); port 6c4024f pattern over when touched next

**Notes for other environments:**
- Product thinking lives in ~/living-draft/SPEC.md; treat it as the source of truth for the offering discussion