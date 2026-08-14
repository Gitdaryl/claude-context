## Session: 2026-08-14 ET
**Environment:** Antigravity IDE

**What was done:**
- Built the live agent status board: `api/lib/cronHeartbeat.js` + `api/status-agents.js` on Manitou Beach, hooked into `requireCron()` so all 18 crons get observability from one file change instead of 18 edits
- Kept `requireCron()` synchronous deliberately. Callers do `if (!requireCron(req, res)) return`, so returning a Promise would be truthy on every path and silently turn the guard into an auth bypass on every cron endpoint
- Wired the positioning page's agent table to that endpoint as pure progressive enhancement: every failure path is a silent no-op, so a fetch error, CORS problem, cold KV, or full platform outage all degrade to the static table already in the HTML
- Added site section 04 "Who gets to cite your company", framing AI crawler policy as governance rather than SEO, grounded in artifacts verified live (llms.txt 200, robots.txt directives for GPTBot/ClaudeBot/PerplexityBot/Google-Extended)
- Found and fixed a CORS cache-poisoning bug I shipped myself: per-origin ACAO on an edge-cached endpoint meant whichever request filled the cache first decided the header everyone got

**What's live / deployed:**
- **https://work.yetigroove.com** live, TLS cert `CN=work.yetigroove.com` valid to Nov 12 2026, serving `X-Robots-Tag: noindex, nofollow` plus `Referrer-Policy: no-referrer`
- Private repo `Gitdaryl/yeti-positioning`, visibility confirmed PRIVATE
- Manitou Beach `GET /api/status-agents` live, `tracking: true`, static `Access-Control-Allow-Origin: *`
- Heartbeat write path proven end to end: `qa-agent` fired on its 30 min schedule and recorded
- Agent table verified upgrading in a real browser: `qa-agent / RAN 14 MIN AGO`, header reads `18 ACTIVE / LIVE`

**Next up:**
- Fill the five missing numbers in SOURCE-DOC section 3: MAU, paying businesses, MRR, ops hours displaced, client retention. These are worth more than any additional copy
- Rewrite LinkedIn from SOURCE-DOC section 8, enable Open To Work recruiters-only
- Agent table fills in over roughly a month as each cron next fires: daily jobs tomorrow, weekly within a week, monthly up to 31 days
- Manitou Beach has **uncommitted work** sitting in it (gallery components, `middleware.js`, `car-identify.js`, `health.js`) that did not deploy
- `www.yetigroove.com` is CNAME'd to Vercel as **Proxied** in Cloudflare, which is the config behind the 5xx body masking. Worth revisiting separately

**Notes for other environments:**
- SOURCE-DOC.md is the single source. Edit it first, then re-render the site and LinkedIn. Never write positioning copy anywhere else first
- SOURCE-DOC.md is private and must never be sent to anyone. It contains the salary floor and known weaknesses
- Never password-protect job-search pages. Unlisted + noindex only, and robots.txt must allow crawling or the noindex is never read
- On edge-cached endpoints, CORS headers must not vary by request origin. See the new cors-allowlist-cdn-cache-poisoning memory