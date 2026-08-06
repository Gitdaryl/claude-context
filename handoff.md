## Session: 2026-08-05 ET
**Environment:** Antigravity IDE

**What was done:**
- Reviewed Joe Profit's modified reel (`Joe_Profit_Reel_V2_Higher_Compatible.mp4`). Four real defects, not opinion: the book cover PNG covers the burned-in captions the whole way through, the video was shrunk into a letterbox so Joe's face is ~35% of frame, the footer bar sits in the bottom 25% where Instagram and TikTok paint the caption and action buttons, and the book appears twice on the end card.
- Built `brand-kit/` in the Joe-Profit repo as the replacement approach.
  - Rebuilt the 40 / Never Broken / Always Forward seal as vector `src/seal.svg`. No source file for it existed before; it only lived baked into Joe's footer bitmap.
  - Drop-in overlays, all 1080x1920, placed at 0,0 with no repositioning: corner lockup, seal-only variant, end card, bottom scrim, standalone seal.
  - `build.sh` renders the PNGs from HTML/SVG via headless Chrome.
  - `apply-lockup.sh` keeps video full frame (crop, never pad), fades the end card in over the last 4s with audio untouched so a spoken CTA plays over it, batch capable.
  - `audiogram.sh` turns long audio into short vertical clips: push-in still, gold waveform, title, loudnorm to -16 LUFS, optional SRT burn-in.
- Drafted a reply to Joe and a scope fix: one production block a month with Joe ranking his own list, only accept work that leaves a reusable template, replace the unrealised 10%-of-speaking-fees handshake with two warm intros a quarter.

**What's live / deployed:**
- Pushed to `github.com/Gitdaryl/Joe-Profit` main, commit `d7fbe44`, under `brand-kit/`.
- Drop-in PNGs copied to `~/Desktop/JoeProfit-BrandKit-DropIn/`.
- Sample branded reel at `~/Desktop/Joe_Profit_Reel_V3_YetiGroove.mp4` (90s, 1080x1920, 60MB).

**Next up:**
- Send Joe the V3 sample plus the drafted reply.
- Propose the CTA test: five reels his way (35-45 spoken words) against five at 12-18 words, compared on watch time and link taps.
- Chase the podcast outreach. It is the highest-value item on the list and only Joe can do it.
- Cut the radio interview into roughly six 45-second clips with `audiogram.sh` rather than one 15-minute video.

**Notes for other environments:**
- Two ffmpeg traps found the hard way, both documented in `brand-kit/README.md` and worth reusing on any client video work:
  1. Thin coloured lines turn green in yuv420p. `showwaves` draws 1px hairlines and 4:2:0 chroma subsampling averages them with the black behind, so gold collapses to muddy green. Render the waveform small and scale up with `flags=neighbor` for chunky bars that survive the encode.
  2. ffmpeg consumes stdin. Inside a `while read` loop it swallows the rest of the input file and silently skips every item after the first. `-nostdin` fixes it.
- Both tools are client-agnostic. Swap `assets/never-broken-cover.png` and the text in `src/lockup.html` and the same kit works for Mitchel Ramsey, Sunny Skies or the Men's Club.