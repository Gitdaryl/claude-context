
## Session: 2026-09-16 ET
**Environment:** Antigravity IDE
**What was done:**
- Audited all site repos for image format: galleries were WebP, everything else JPG/PNG with no build-time conversion anywhere.
- Built `~/.claude/tools/webp-sweep.py` (ImageMagick, q80, max 1920px, rewrites refs, protects OG/favicon/PWA/email/middleware refs, skips unreferenced files).
- Ran it on Manitou-Beach (57 MB -> 16 MB, 160 images, 44 files rewritten, 0 broken images across 7 pages headless) and Spotted Owl (3.2 MB -> 1.6 MB, OG image 1.8 MB png -> 248 KB jpg).
- Made it SOP: Step 0 of the `commit-push` skill on every project + "Build Standard: Image Weight" section in ~/.claude/CLAUDE.md.

**What's live / deployed:**
- Manitou-Beach main pushed (rebased over two upstream gallery-retag commits); Vercel git deploy in progress at session end.
- Spotted Owl pushed and CLI-deployed to spotted-owl-site.vercel.app, WebP verified live.

**Next up:**
- Yeti-Groove has 78 JPG/PNG (mostly `_src` originals, ~5 served); sweep will catch the served ones on next push.
- Manitou galleries keep 270 JPG twins in the repo (only `-01.jpg` used for OG); pruning them would cut ~100 MB of repo weight but is not page weight. Optional.

**Notes for other environments:**
- Cowork/Mobile: if adding images to any site, drop JPG/PNG in; the IDE's push converts them. Do not hand-convert.