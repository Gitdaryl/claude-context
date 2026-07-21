## Session: July 21, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Finished the crowd-photo share card investigation on the Manitou Beach site (commits f49c543, 9ba665c, d1643bb, all live)
- Full OG chain now works: stable photo-id links, server-side per-photo og:image via middleware on both /gallery/:slug and wall pages (/america-250, /mens-club, /ladies-club), og:image:width/height declared so first shares render the image
- Meta Sharing Debugger renders the complete photo card (200, correct og:image, preview with photo)
- Yeti ran the isolation matrix: YouTube previews in the same Messenger chat (works), FB post composer shows our photo card (works), WhatsApp/iMessage show the card (works). Messenger alone suppresses previews for the domain = Messenger's domain-reputation filter, not our code. Expected to clear with legitimate share volume
- Saved memory: messenger-og-preview-quirk (3-test matrix + OG lessons)

**What's live / deployed:**
- f49c543 + 9ba665c + d1643bb on Gitdaryl/Manitou-Beach main → Vercel, verified

**Next up:**
- Optional: verify manitoubeachmichigan.com in Meta Business Suite (Settings → Brand Safety → Domains, DNS TXT) to build domain trust
- Share the America 250 gallery as a Facebook post for reach (that path renders the photo card today)
- Still open from July 20: finish uploading/tagging America 250 photos; paste the YouTube URL into USA250_FILM_URL when the film is live

**Notes for other environments:**
- If a client says "my link doesn't preview in Messenger": run the 3-test matrix (YouTube link same chat / FB post composer / WhatsApp) before touching code