## Session: 2026-08-14 ET
**Environment:** Antigravity IDE

**What was done:**
- Built the live agent status board: `api/lib/cronHeartbeat.js` + `api/status-agents.js` on Manitou Beach, hooked into `requireCron()` so all 18 crons get observability from one file change instead of 18 edits
- Kept `requireCron()` synchronous deliberately. Callers do `if (!requireCron(req, res)) return`, so returning a Promise would be truthy on every path and silently turn the guard into an auth bypass
- Added a traced-path SVG to the positioning page: three real transactions (revenue, content, trust) collapsing into "THREE ROLES / One operator". Deliberately not a hub-and-spoke stack diagram, which reads as bus-factor-of-one on a hiring page
- Rewrote the page outcome-first (Levitt: sell the hole, not the drill bit) after Yeti's critique. One plain-language outcome line per section, evidence second
- Added site section 04 framing AI crawler policy as governance, not SEO
- Built **yetigroove.com/platform**, the client-facing hub-and-spoke sales board, in the gold/ink brand
- Fixed a CORS cache-poisoning bug I shipped: per-origin ACAO on an edge-cached endpoint meant whichever request filled the cache first decided the header everyone got
- Searched live fractional and full-time AI leadership roles. Found and drafted an application for **WongDoody, Head of AI North America**, $225-250k remote

**What's live / deployed:**
- **https://work.yetigroove.com** — hiring page. TLS valid to Nov 12 2026, `X-Robots-Tag: noindex`, live agent table verified upgrading in a real browser
- **https://www.yetigroove.com/platform** — client sales board, noindex, clean URL rewrite added to `vercel.json`
- Manitou Beach `GET /api/status-agents` live, `tracking: true`, static `Access-Control-Allow-Origin: *`
- Private repo `Gitdaryl/yeti-positioning`, visibility confirmed PRIVATE

**Next up:**
1. **Submit the WongDoody application.** Draft ready at `~/Projects/yeti-positioning/applications/wongdoody-head-of-ai.md`. Role is live and hiring windows close. Greenhouse asks years of professional AI experience: answer **2**
2. **Ship a retrieval layer on the Manitou Beach voice concierge.** Vector databases are the ONLY genuine technical gap on WongDoody's requirement list. MB has 30 Notion databases and a live ElevenLabs concierge answering from a static knowledge base. Adding embeddings so it retrieves across events, businesses and articles is roughly a weekend, measurably improves the concierge, and converts "I would pick it up" into "I added retrieval to a production voice agent." Do this while the application sits in their queue
3. Sign up to fractionaljobs.io (open registration, they pre-screen). 50+ live roles, comparable ones at $8-10K/mo for 10-15 hrs/week
4. Fill the five missing numbers in SOURCE-DOC section 3: MAU, paying businesses, MRR, ops hours displaced, retention
5. Rewrite LinkedIn from SOURCE-DOC section 8, enable Open To Work recruiters-only
6. Manitou Beach has **uncommitted work** sitting in it (gallery components, `middleware.js`, `car-identify.js`, `health.js`) that did not deploy

**Notes for other environments:**
- SOURCE-DOC.md is the single source. Edit it first, then re-render site and LinkedIn. It is private and must never be sent to anyone, it holds the salary floor and known weaknesses
- Job aggregators keep dead postings live for SEO. Two "actively hiring 2026" fractional CAIO roles turned out to be March 2024 and closed. Always fetch the actual posting, never trust a search summary on currency
- Titles containing "Chief AI Officer" skew toward ML practitioners and demand advanced degrees. "Head of AI" at agencies screens on applied outcomes. Chase the second
- Fractional market rate is **$15-25K/mo**, higher than the $8-15K first estimated. Source doc updated
- Never password-protect job-search pages. Unlisted + noindex only
- On edge-cached endpoints, CORS headers must not vary by request origin