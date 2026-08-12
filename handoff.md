## Session: 2026-08-12 ET
**Environment:** Antigravity IDE

**What was done:**
- Installed the Higgsfield CLI (`@higgsfield/cli` v1.1.23), Yeti authenticated, workspace "Private" (`5d35139d-6457-4a9d-b5e4-ad3036bacab1`, ultimate plan) selected. Gotcha: `higgsfield account status` errors "No workspace selected" until you run `hf workspace set <id>`.
- Installed 8 `higgsfield-*` skills + `oso95/scroll-world` into `~/.claude/skills/` via `npx skills add ... -a claude-code`. The agent flag is `claude-code`, NOT `claude`.
- Installed the Monid CLI (`@monid-ai/cli` v0.1.6). **Still needs `monid keys add` + a funded balance from Yeti.**
- Assessed scroll-world against Yeti's use cases. Verdict: strong for previz/unbuilt developments, roofing, software, trades, personal branding. Wrong tool for renovation render inquiries (different deliverable) and for flying a camera through an existing listed house (the still is accurate, but Seedance invents geometry between frames). Best first build = `/signature`, photoreal Architecture A, because previz of unbuilt land has no ground truth to violate.
- Audited yetigroove.com headless (Playwright). Found the reel playing with Chrome's default control bar, and the hero at 720p.
- **Fixed the reel player** in `index.html`: custom gold play affordance replaces native controls, native controls hand back once playing. Progressive enhancement (markup keeps `controls`, JS strips it), keyboard focusable, reduced-motion branch. Verified in-browser: no console errors, click starts playback, overlay fades.
- **Upscaled the hero with Topaz** (`topaz_video`, 2160p) for **6 credits** (345.11 -> 339.11). Re-cut all 49 scrub frames at 1920x1080 (was 1280x720), new poster, and re-encoded the mobile fallback mp4 at 1080p. Verified the scrub still runs: `scrub-active`, no 404s, no errors.

**What's live / deployed:**
- Nothing deployed. **52 files modified in `~/Projects/Yeti-Groove`, uncommitted**, awaiting Yeti's go-ahead.

**Next up:**
- Deploy decision on the Yeti-Groove changes (commit + push, Vercel).
- `monid keys add` and fund, if the scroll-world build goes ahead.
- Then the `/signature` scroll-world build: 3 scenes, photoreal, 480p draft first.

**Notes for other environments:**
- Two corrections worth carrying: (1) the 49 webp frames are NOT orphans, they ARE the desktop scrub (canvas frame sequence); the mp4 is the mobile/reduced-motion fallback. (2) There is no higher-res master of the yeti rise anywhere on disk; `~/Downloads/Yeti groove in water.mp4` is the 720p source. Topaz was the only path.
- Topaz upscale is cheap (6 credits for a 4s clip at 4K). Video generation is 40-55 credits by comparison. Useful for lifting any older 720p client footage.
- Frame payload went 3.0MB -> 5.7MB, desktop-only (mobile takes the mp4 path), streamed after the LCP frame. The 1080p mp4 is 2.5MB, smaller than the 720p it replaced.