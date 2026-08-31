## Session: Aug 31 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Rewrote the end of both signups to hand over controls instead of pointing at the public locator. New shared modules: ControlHandoff.jsx, HomeScreenInstall.jsx (one copy of the install logic, was about to be three), controlSurfaces.js (new verticals are a data key, not a screen)
- Wrote the Vendor Control Plane report: plumbing diagram, four POVs, ranked vulnerabilities, modularity layers. https://claude.ai/code/artifact/cec71906-af2f-464f-9013-53dff87e4f33
- Auto-pin now ASKS permission instead of announcing after the fact. Consent is per day, silence means no, reply Y/N by text. Three unanswered weekends stops the asking and alerts Daryl once. Vendors choose: ask me first (default) / just do it / leave it to me. Every truck including Wieners defaults to being asked, per Yeti - a weekly decision teaches them it is their tool.
- 'Skip Social' is now a real switch (map only, never post me), honoured in food-trucks.js
- Weekly systems check: seven credential checks in plain English, each carrying either numbered steps or a copy-paste message for Claude. Runs Mondays, retries before crying wolf, remembers last week so it can say "this fixed itself". ?preview=1 renders the alert as if everything failed.

**What's live / deployed:**
- Three commits pushed to main and deployed. Verified live: settings panel renders and saves (tested set/read/restore against production, wrong token refused), all seven health checks pass against production credentials including Facebook.

**Next up:**
- Store the Meta post id so checkout can retract a wrong announcement (highest value open item)
- Vendor token regeneration (the only permanent credential in the system)
- Rate limit the food truck write path
- "Right now" live panel: trucks out, bands playing, events starting within the half hour. NOT a marquee, and it must never render empty
- Then the lineup engine: confirm-to-pin, approver role, outreach queue

**Notes for other environments:**
- CRON_SECRET and ADMIN_SECRET in the local .env.notion.tmp are both stale (production rejects them), so cron admin/dry-run endpoints cannot be triggered from this Mac. Third-party keys in that dump are still valid. Yeti evidently rotated the two he controls.
- Only ONE secret in the whole project expires on a clock: the Meta page token. Everything else rotates on exposure only. Recommended against automating rotation - it needs a Vercel API token that can rewrite every env var, a bigger key than the ones it protects.
- Delete .env.notion.tmp when not in use. Gitignored and never committed (checked), but it is a full copy of production secrets on disk.