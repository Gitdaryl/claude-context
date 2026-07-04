
## Session addendum: 2026-07-04 ET (device-aware share fix)
**Problem found in testing:** iOS native share of {title,text,url,files} sent only the text (no photo, no link) to Messages — classic iOS Web Share mangling when mixing image file + link + text.
**Fix:** ShareRow (src/components/PhotoGallery.jsx) is now device-aware:
- Mobile (coarse pointer + navigator.share): one "Share" button (native sheet) that shares the BARE URL only -> recipient app renders the per-photo OG card (photo preview + tappable link = traffic). Plus a Copy link button. No more file/text mixing.
- Desktop: explicit icon row (FB/X/WhatsApp/Email/Copy) where web-share links behave.
- Dropped image-file sharing (was unreliable; link-with-OG-card is better for traffic anyway). If Yeti later wants to post the actual image to Instagram, that's a separate feature.
- Build passed, pushed to main (9cca4ee).
**Note:** mb-context skill is STALE — claims App.jsx is a monolith, but repo is split into src/pages/* + src/components/*. Worth updating that skill.