## Session: 2026-08-14 ET
**Environment:** Antigravity IDE

**What was done:**
- Assessed realistic CAIO / Head of AI positioning from a repo audit, not self-report. Verified: 900 commits, 173 production endpoints, 18 autonomous cron agents, 12 LLM-backed endpoints, 27 Stripe endpoints, production ElevenLabs concierge
- Wrote `SOURCE-DOC.md`, the master positioning doc, and shipped an unlisted noindex site rendered from it
- Built cron heartbeats + `/api/status-agents` on Manitou Beach so the site's agent table shows real last-run times. Hooked into `requireCron()`, the single choke point all 18 crons pass through
- Added a traced-path SVG (revenue / content / trust) collapsing into "THREE ROLES, One operator", and a governance section on AI crawler policy
- Rewrote the page outcome-first after Yeti's Levitt critique: sell the hole, not the drill bit
- Built **yetigroove.com/platform**, the client-facing hub-and-spoke sales board
- Found and drafted the **WongDoody Head of AI** application ($225-250k, remote)
- **LinkedIn rebuilt end to end:** headline, About, Skills, experience bullets, Featured card, banner, first post published, Open To Work configured
- Fixed a CORS cache-poisoning bug I shipped: per-origin ACAO on an edge-cached endpoint meant whichever request filled the cache first decided the header everyone got

**What's live / deployed:**
- **https://work.yetigroove.com** — hiring page. noindex, TLS to Nov 12 2026, live agent table, og:image card verified
- **https://www.yetigroove.com/platform** — client sales board, noindex, rewrite added to `vercel.json`
- Manitou Beach `GET /api/status-agents`, `tracking: true`, static `Access-Control-Allow-Origin: *`
- **LinkedIn profile live and consistent** with the site: headline with full keywords, Featured card rendering the OG image, banner in the same visual language, persist-before-notify post published, Contract + Part-time ticked, recruiters-only visibility, Bitcoin Profits entry removed
- Private repo `Gitdaryl/yeti-positioning` (confirmed PRIVATE)

**Next up, in this order:**
1. **Submit WongDoody.** Everything it depends on is now in place. Draft at `~/Projects/yeti-positioning/applications/wongdoody-head-of-ai.md`. Greenhouse asks years of professional AI experience: answer **2** (Feb 2024 start supports it)
2. **Ship a retrieval layer on the MB voice concierge.** Vector DBs are the only genuine technical gap on WongDoody's requirement list. MB has 30 Notion databases and a concierge answering from a static knowledge base. Roughly a weekend, genuinely improves the product, converts "I'd pick it up" into "I added retrieval to a production voice agent." Do it while the application sits in their queue
3. Sign up to fractionaljobs.io (open registration, pre-screened, 50+ live roles)
4. Fill the five missing numbers in SOURCE-DOC section 3: MAU, paying businesses, MRR, ops hours displaced, retention. Still the single highest-value addition to the whole kit
5. Small LinkedIn leftovers: switch "Flexible, casually looking" to "Immediately, actively applying"; fix "winnning" typo in the Snow Dragon entry; optionally remove the Yevo International entry
6. Manitou Beach has **uncommitted work** (gallery components, `middleware.js`, `car-identify.js`, `health.js`) that did not deploy

**Notes for other environments:**
- SOURCE-DOC.md is the single source. Edit it first, then re-render site and LinkedIn. Private, never send it, it holds the salary floor and known weaknesses
- Build artifacts are reproducible, not hand-made: `og-source.html` and `banner-source.html` render via headless chrome. Re-render when numbers change, never hand-edit a PNG. LinkedIn banner: avatar covers the first 460px, content starts at 520px
- **Job title:** do NOT use "Head of AI" as the LinkedIn experience title at his own studio. Reads as self-awarded. `Founder / AI Systems and Production`. Head of AI goes in Open To Work titles, which is the field Recruiter searches
- Job aggregators keep dead postings live for SEO. Two "actively hiring 2026" fractional CAIO roles were March 2024 and filled. Always fetch the posting, never trust a search summary on currency
- Chase "Head of AI", not "Chief AI Officer". CAIO postings demand advanced degrees and ML frameworks
- Fractional market rate is **$15-25K/mo**, not the $8-15K first estimated
- Never password-protect job-search pages. Unlisted + noindex, and robots.txt must ALLOW crawling or the noindex is never read and link previews break too
- On edge-cached endpoints, CORS headers must not vary by request origin