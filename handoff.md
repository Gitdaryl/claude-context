## Session: 2026-08-12 ET
**Environment:** Antigravity IDE

**What was done:**
- Installed + authed the Higgsfield CLI (`@higgsfield/cli` v1.1.23), workspace "Private" (ultimate). Installed the Monid CLI (`@monid-ai/cli`) — **still needs `monid keys add` + funding**. Installed 8 `higgsfield-*` skills + `oso95/scroll-world` into `~/.claude/skills/`.
- Two install gotchas: skills CLI agent flag is `claude-code` NOT `claude`; and `higgsfield account status` errors "No workspace selected" until `hf workspace set <id>`.
- scroll-world fit assessment: strong for previz/unbuilt developments, roofing, software, trades, personal branding. Wrong tool for the two renovation *render* inquiries (different deliverable) and for flying a camera through an existing listed house (the still is accurate, Seedance invents geometry between frames). Best first build = `/signature`, photoreal Architecture A.
- **Shipped to yetigroove.com (2 commits):**
  - `738d68b` — custom reel play button replacing Chrome's default control bar (progressive enhancement, keyboard focusable, reduced-motion branch). Homepage hero via Topaz 2160p (6 credits): 49 frames 1280x720 -> 1920x1080, mp4 fallback 720p/2.7MB -> 1080p/2.5MB.
  - `d2dae7f` — `/signature` hero via Topaz 2160p (11 credits): 65 frames 1088x612 -> 1600x900, mp4 fallback 4.3MB -> 3.0MB at 720p from the 4K master.
- Credits: 345.11 -> 328.11 (17 total for both upscales).

**What's live / deployed:**
- yetigroove.com through `d2dae7f`. Homepage verified in production (frame_001 138604b, mp4 2600464b, scrub-active, custom play button, 49 frame requests, zero console errors). **/signature deploy was still propagating at hand-off — re-verify `frame_001.webp` is 152770b, not 69910b.**

**Next up:**
- Confirm the /signature deploy landed.
- `monid keys add` + fund, then the `/signature` scroll-world build: 3 scenes, photoreal, 480p draft first.

**Notes for other environments:**
- Topaz cost scales with frame count: 6 credits for 97 frames, 11 for 194. Cheap enough to lift any old 720p client footage. Video *generation* is 40-55 by comparison.
- Corrections worth carrying: the webp frame sets ARE the desktop scrub (canvas sequence), not orphans; the mp4s are the mobile/reduced-motion fallback. No HD masters exist for either hero. And ffprobe's `r_frame_rate` lies on these files (reports 48fps on an 8.1s/194-frame clip) — trust `format=duration`, and Topaz preserved timing exactly.
- Frame payload is resolution-bound, not quality-bound: on the dense drone footage, webp q76->q48 only moved 15MB->11MB. AVIF saved ~25%, all-intra h264 for blob-seek was 27MB. 1600x900 was chosen because 1088->1600 carries nearly all the visible gain and 1600->1920 costs 5MB for nothing visible in motion.