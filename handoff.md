
## Session (cont. 3): 2026-09-30 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD: scroll-scrubbed logo hero (shipped), review pass (8 fixes), rain with card splashes, /partners page, BBB reviews section (4 verbatim, no average), cache-busting (tools/stamp_assets.py)

**What's live / deployed:**
- onpointjd.com, /snow, /partners

**Next up (Oct 1):**
- Twilio number -> crew alerts, customer texts, missed-call text-back, restore "text within a minute" copy
- Drone photos into site/assets/photos/ + job captions
- Devon: unify Google/BBB/FB name + new logo + add website; Jay: reply to 2-star BBB review; ask recent customers for Google reviews
- Ask Jay: warranty/certification, financing, insurance (COI) wording, SE Michigan
- Print templates (yard sign first)

**Notes for other environments:**
- Deploy = stamp_assets.py, commit, push, vercel deploy --prod (site/)