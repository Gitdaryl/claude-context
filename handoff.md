
## Session: 2026-11-09 ET
**Environment:** Antigravity IDE
**What was done:**
- Studied the FB reel "20 video effects in 20 seconds, built by Claude" at 10 fps; catalogued 21 effects with when-to-use guidance
- Built ~/.claude/tools/fx/: fx_cutout.sh (HyperFrames remove-background on Node 22) and fx_track.py (MediaPipe face/head/hand JSON), both tested on the reel
- New skill reel-fx (~/.claude/skills/reel-fx/SKILL.md) + memory reel-fx-menu so effects get suggested during reel brainstorming

**What's live / deployed:**
- Nothing deployed; local tools and skill only

**Next up:**
- Build each effect as a HyperFrames template the first time it is used (none built yet); first proof: Letter dive, Sketch words, Blow away on a real talking clip

**Notes for other environments:**
- HyperFrames needs Node 22; shell default is Node 20 (use fx_cutout.sh or nvm use 22)
- Shoot tip for any talking head: tripod, no moves, hold 5 s of empty set at end of take