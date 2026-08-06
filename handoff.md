## Session: Aug 5, 2026 ET (PWA install)
**Environment:** Antigravity IDE
**What was done:**
- Made Idea Greenhouse an installable PWA so Holly (and Yeti) can add it to their phone home screens instead of digging the link out of messages.
- Added manifest.webmanifest (standalone display, greenhouse theme colors), 192/512/maskable icons plus apple-touch-icon (seedling emoji on the greenhouse gradient, rendered via headless Chrome), iOS standalone meta tags, and a network-first service worker (always fresh when online, cached fallback offline, never touches /api/ requests so no stale data or masked deploys).
- Verified live: manifest serves with correct content type, service worker registers, all three icons 200.

**What's live / deployed:**
- idea-greenhouse-pi.vercel.app, commit 2d8a7d4 on Gitdaryl/idea-greenhouse main.

**Next up:**
- Optional: Plant It date field; my-tasks filter per person.

**Notes for other environments:**
- Install steps to pass to Holly: iPhone: open idea-greenhouse-pi.vercel.app in Safari, tap Share, "Add to Home Screen". Android: open in Chrome, tap the three-dot menu, "Add to Home screen" / "Install app". Opens full-screen with a seedling icon named "Greenhouse". Login is remembered per device (she enters growroom-2026 + picks Holly once).