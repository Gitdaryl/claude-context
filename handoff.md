
## Session addendum: 2026-07-04 ET (lightbox swipe gestures)
- Confirmed per-photo OG previews WORK live (curl showed correct og:image; a never-before-shared 2025 photo rendered the real photo card in Messenger). Earlier logo cards = Facebook's per-URL cache from prior scrapes; re-scrape via FB Sharing Debugger or share a fresh photo.
- Added useSwipeNav hook (src/components/PhotoGallery.jsx): swipe L/R = prev/next, swipe down = close. Applied to both PhotoGallery lightbox and Ladies Club lightbox. touchAction:none on container. Taps <45px still fire buttons.
- Build passed, pushed to main (34ac52c).