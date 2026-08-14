## Session: 2026-08-13 ET
**Environment:** Antigravity IDE

**What was done:**
- Assessed Yeti's realistic positioning for a CAIO / Head of AI job search, grounded in an audit of the actual repos rather than self-report
- Verified hard numbers from Manitou-Beach: 900 commits, 173 production API endpoints, 18 autonomous scheduled agent jobs, 12 LLM-backed endpoints, 27 Stripe endpoints, production ElevenLabs voice agent
- Researched LinkedIn tooling. Conclusion: no official MCP or CLI exists, the official API cannot write profile fields at all, and browser-session scrapers risk the account. Profile editing stays manual
- Wrote `~/Projects/yeti-positioning/SOURCE-DOC.md`, the master positioning doc: 3 case studies, LinkedIn render, resume bullets, interview answers, comp targets
- Built and shipped an unlisted one-page site rendered from it, verified live by headless screenshot at desktop and mobile
- Fixed two defects found only by screenshotting: metrics band gradient bleeding past the content column, and an em dash in the page title

**What's live / deployed:**
- Private repo `Gitdaryl/yeti-positioning` (visibility confirmed PRIVATE)
- https://yeti-positioning.vercel.app, publicly reachable with no auth wall, serving `X-Robots-Tag: noindex, nofollow` plus `Referrer-Policy: no-referrer`
- `work.yetigroove.com` added to the Vercel project, **not yet resolving**

**Next up:**
- Yeti to add Cloudflare A record: `work` -> `76.76.21.21`, **DNS-only / grey cloud, not proxied**
- Fill the five missing numbers in SOURCE-DOC section 3: MAU, paying businesses, MRR, ops hours displaced, client retention
- Rewrite LinkedIn headline / About / Skills / experience from SOURCE-DOC section 8, enable Open To Work recruiters-only
- Get verbal OK from a client before naming them in a case study

**Notes for other environments:**
- SOURCE-DOC.md is the single source. Never write positioning copy anywhere else first, re-render from it
- SOURCE-DOC.md is private and must never be sent to anyone. It contains the salary floor and the known weaknesses
- Do not password-protect job-search pages. Unlisted + noindex only, and robots.txt must allow crawling or the noindex directive is never read