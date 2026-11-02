
## Session: 2026-11-02 ET
**Environment:** Claude Code (VS Code extension)
**What was done:**
- Holly NFC keyring: added /review/tap, /review/qr, /review redirects (api/review-tap.js + vercel.json) to her Google write-review link, counted per tap in Blob (taps/review/<via>/). Yeti wrote the chip with https://hollygriewahn.vercel.app/review/tap.
- Holly seller pitch: /why-holly (src/pages/WhyHollyPage.jsx), scroll mode + Present mode (/why-holly?present=1), 11 slides, comparison column written as "ask them" questions, all stats computed from data/fetched live. Built by an Opus subagent, verified by Claude. Added "Why Holly" to SiteNav (hamburger breakpoint moved 768 to 920px), prerender block, llms.txt entry, motion.css keyframes.

**What's live / deployed:**
- b39f5d3 (review redirect) and a0f01c8 (/why-holly) pushed to Gitdaryl/Holly main; both confirmed live on hollygriewahn.vercel.app (prerendered HTML + 302 checked via curl).

**Next up:**
- Confirm tap counts: /api/review-tap?report=1 with ADMIN_SECRET (not verified; no key access).
- Optional: show review tap counts on Holly's desk Stats tab.
- Live browser check of Present mode on the deployed URL (only curl-checked after deploy; Playwright was run on local build).
- /sell page claims showing-feedback summaries that are NOT built; fix the copy or build the feature.
- Desktop hero on /why-holly leaves right side empty; two slides scroll inside the slide on phones.
- Waitlist is empty in prod, so lake picker shows invitation wording, not buyer counts.

**Notes for other environments:**
- Pitch page deliberately makes no price promise; Monday update sample card uses made-up numbers labelled "Sample".