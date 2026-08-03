## Session: Aug 3, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Built and shipped TWO scroll-scrub heroes for yetigroove.com:
- Homepage: photoreal Yeti rises from Devils Lake at dawn cranking a vintage 35mm camera with "YETI GROOVE" nameplate. Nano Banana Pro (character refs: realistic cafe Yeti + cartoon front-on) + Seedance 2.0 animation. 49 webp frames, 280vh pinned scrub.
- /signature: the Cove builds itself as you scroll. Generated a missing "empty excavated basin" frame at the same aerial angle as the existing build/complete previz stills, then two Seedance start/end morphs (empty>framing, framing>complete-at-dusk). 65 frames over 380vh, "SCROLL TO BUILD IT" hint, headline lands on the finished village. The hero literally demos the previz product.
- Both: canvas scrub with nearest-loaded-frame drawing, shade/text reveal tied to scroll, mobile/reduced-motion/save-data fall back to self-hosted looping mp4s. Homepage no longer depends on the cove app for hero video.
- Verified with headless Playwright locally and live both times.

**What's live / deployed:**
- yetigroove.com hero scrub (commit 1be3159), /signature build scrub (commit f3b38d3), repo Gitdaryl/Yeti-Groove

**Next up:**
- Nothing pending; alternate hero takes saved in Desktop/Yeti-Groove/Assets/scroll-scrub-hero-tests/ (incl. rejected Mickey-logo variant, trademark risk)

**Notes for other environments:**
- Character/scene gen recipe saved to memory: Nano Banana Pro for "same character/scene, new state"; Soul 2 clones the whole reference scene. Seedance start_image+end_image morphs are the tool for before/after previz sequences.