## Session: July 21, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Continued the crowd-photo share card fix on the Manitou Beach site (commit d1643bb, follows f49c543 + 9ba665c earlier today)
- Even with correct OG tags, Messenger still rendered no image. Root cause: Facebook renders the FIRST share of a new URL without an image unless og:image:width/height are declared (it fetches the picture async), and every fresh photo link is a first share
- Middleware now injects og:image:width/height from the dimensions captured at upload time, for both /gallery/:slug?photo= and wall-hosting pages (/america-250, /mens-club, /ladies-club)
- Verified live as facebookexternalhit: full og:image block (url, secure_url, type, width 1600, height 902) on both URL forms

**What's live / deployed:**
- f49c543 + 9ba665c + d1643bb on Gitdaryl/Manitou-Beach main → Vercel, all verified live

**Next up:**
- Yeti to retest with a photo link he has NOT shared before (Messenger caches per URL)
- If a card still doesn't render: check the link in developers.facebook.com/tools/debug (shows exactly what FB sees + any errors); remaining suspect would be Messenger end-to-end-encrypted chat preview quirks, not our tags
- Still open from July 20: finish uploading/tagging America 250 photos; paste the YouTube URL into USA250_FILM_URL when the film is live

**Notes for other environments:**
- Photo share OG chain is now: stable id links → middleware resolves photo via /api/photos-list → og:image + dimensions injected server-side