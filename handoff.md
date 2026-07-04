
## Session addendum: 2026-07-04 ET (finger-follow carousel lightbox)
- Slide-in animation wasn't native enough; built a real finger-follow carousel.
- New shared Lightbox component in src/components/PhotoGallery.jsx: 3-slide window (prev/current/next), track follows finger via translateX(calc(-100vw + dxpx)) during touchmove, snaps to neighbour/back on release (threshold 20% width), swipe down (>90px vertical) closes. Arrows/keyboard animate via same commit(). Neighbours preloaded, body scroll locked, tap-photo keeps open / tap-outside closes.
- CONSOLIDATED: both galleries now use <Lightbox>. Removed Ladies Club's duplicate inline lightbox + the old slide-in (useSwipeNav, LightboxKeyframes, LB_ANIM_* all removed). LadiesClubPage imports only { Lightbox } now.
- Note: separate GalleryLightbox (line ~199, the "What to Expect" swipe cards) is unrelated/pre-existing, left alone.
- Build passed, pushed to main (8f7b533). Needs phone test for gesture feel.