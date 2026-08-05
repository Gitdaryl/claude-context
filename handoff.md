## Session: 2026-08-05 ET
**Environment:** Antigravity IDE

**What was done:**
- Compressed `~/Desktop/Yetis in the groove.mov` (160MB, uncompressed PCM audio) to a web MP4: 44MB, 1080p30, 78 sec, h264/AAC, faststart + byte-range seeking
- Uploaded video + poster to Vercel Blob under `reel/` on the yeti-groove project
- Added a new "The Reel" section to the yetigroove.com homepage above The Work, with six discipline chips (Aerial, Stop Motion, Construction, Trades, Events, Property) framing the mixed footage as range rather than inconsistency
- Removed the duplicate Devils Lake Cove player from the homepage (`/signature#film` already served the identical film.mp4)
- Replaced the whole Cove case-study section with a 2x2 social-proof grid of four real reviews: Holly Hagar Griewahn (Facebook), Michele Henson, Sandi Kerentoff, Karen Stipe (Google, 5 stars each)
- Fixed two latent bugs: no `scroll-margin-top` on sections meant every anchor jump landed under the fixed nav (index.html + signature.html), and the global `footer { text-align: center }` was bleeding into the new quote attributions
- Repointed nav "The Work" and the hero CTA at `#reel`; zero dead in-page anchors remain

**What's live / deployed:**
- yetigroove.com, three commits pushed to Gitdaryl/Yeti-Groove main: `161640e`, `5bf83ca`, `d8b3eb9`
- Page order is now Hero → Reel → Proof → Clients → Doors → Roots → Contact
- Blob assets: `reel/yetis-in-the-groove.mp4`, `reel/yetis-in-the-groove-poster-boat.jpg`

**Next up:**
- Lower-third client tags baked into the reel cuts (NLE work). The discipline chips frame the mix from outside the video, but tags in the edit travel with the file when it's sent to someone who never visits the site
- Export preset fix: the source .mov had uncompressed PCM audio, which is why it was 160MB. Worth changing once in the project export settings rather than re-encoding every time
- The $30k California-comp pull quote is now off the site entirely and is NOT to be republished (see notes below)

**Notes for other environments:**
- Yeti cut the "$30,000 agency quote" line deliberately: it read as bragging and made the price tier sound like a rare event. He wants buyers to read the rate as normal for the studio. Keep the $30k comp as internal pricing intel only, never client-facing copy
- Holly's testimonial is trimmed to start at "From real estate videos to podcasts..." (the full version opens with personal warm-up and contains an em dash). The other three are verbatim