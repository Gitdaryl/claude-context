## Session: Aug 17 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Excitement Software hero (/c/hero/) rebuilt on Dave's feedback ("looks good" = he thought a slow video was loading, not a scrub scroll)
- Autoplay killed. Engine autoplay is now opt-out (`window.AUTOPLAY = false` in c/hero/world.js, honoured in engine/core.js frame()). Film is dead still until he scrolls. Verified: zero drift over 9s headless
- All hero overlays removed: HUD, altimeter ladder, nameplate, CONCEPT stamp, scanlines, end plate, plus the canvas bottom-scrim and vignette. Only the SCROLL cue survives, promoted to the ready light (appears when scrubable, clears on first scroll) and made legible
- engine/core.js now treats every piece of chrome as optional instead of forking a hero engine. All six concept pages smoke-tested clean
- Frames doubled to full native rate: 397 frames (was 199), three tiers - seq1920 24MB / seq1440 18MB / seq900 8MB. Re-encoded from the source .mov with ffmpeg + libwebp
- Canvas now cross-fades between adjacent frames, so the frame index is continuous rather than stepped. Verified: a 7px scroll (a third of a frame) changes the picture, desktop and phone
- Staged loader: coarse-to-fine passes, 6 lanes, every 16th frame first, so the whole timeline is scrubable ~25 files in instead of after 24MB
- Motion interpolation tested and rejected: minterpolate smeared the letters behind the raven in the flight beat. Documented in PRODUCTION.md

**What's live / deployed:**
- https://excitement-software.vercel.app/c/hero/ (deployed twice; second deploy carries the final cue guard). Verified headlessly on the live URL: no chrome, no autoplay drift, 397/397 frames, no console errors
- PRODUCTION.md has a full "Hero rebuild after the first Dave review" section with the re-encode commands

**Next up:**
- Root (/) still rewrites to /c/factory/ in vercel.json. If hero is the concept now, that rewrite should point at /c/hero/
- Dave still owes: the doctrine one-pager, confirmed dates/figures for the PENDING fields, and access@excitementsoftware.com does not exist yet
- Property films (sso/imt/coa) are still 60-frame scrub sequences at 420px; they could get the same frame-rate and cross-fade treatment if the hero lands well

**Notes for other environments:**
- The repo ~/Projects/excitement-software is NOT a git repo. Deploy is `vercel --prod --yes` from the folder. Edits made after the upload starts are silently missing from that deploy - check the live file before claiming it shipped