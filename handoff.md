## Session: Aug 3, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Brainstormed scroll-scrub hero concepts for yetigroove.com; landed on "Yeti rises from Devils Lake at dawn cranking a vintage 35mm camera"
- Generated the hero shot with Higgsfield: Nano Banana Pro for character-consistent frames (using the realistic cafe Yeti + cartoon front-on as refs), Seedance 2.0 for the 4s image-to-video animation
- Camera nameplate branded "YETI GROOVE"; rejected one variant that had a literal Mickey Mouse logo (trademark risk)
- Built canvas scroll-scrub hero in index.html: 49 webp frames (3MB), 280vh pinned scrub, headline/shade/scroll-hint reveal in last stretch
- Mobile / reduced-motion / save-data fall back to looping yeti-rise.mp4 (now self-hosted, no longer pulling the cove app's hero video)
- Verified locally with Playwright (desktop scrub + mobile fallback + zero console errors), pushed, verified live

**What's live / deployed:**
- yetigroove.com hero scroll-scrub, commit 1be3159 on Gitdaryl/Yeti-Groove

**Next up:**
- Consider scrub heroes for /signature (the "building assembles from empty land" concept demos the previz product)
- All test frames saved in Desktop/Yeti-Groove/Assets/scroll-scrub-hero-tests/ if Yeti wants a different take

**Notes for other environments:**
- Character-gen lesson: Higgsfield Soul 2 treats a reference image as scene/style and will rebuild the whole reference scene; Nano Banana Pro is the right model for "same character, new scene." Refs that work: "yeti realistic .jpg" (cafe) + "Yeti front on.png" (cartoon canon).