## Session: 2026-08-05 (ET)
**Environment:** Antigravity IDE

**What was done:**
- Boathouse winery card on manitoubeachmichigan.com/wineries had NO photos array at all - it rendered logo-only. Fixed.
- Pulled 10 stills off the OSMO SD card (DJI_20260805_0011-0021, shot 14:32-14:35 that day). Working copies + previews in ~/Desktop/boathouse-photos/. DNG raws also on the card if a redo is ever needed.
- Relit 3 bottle shots via Higgsfield (Nano Banana Pro, 2K, 3:2, reference-driven so the real Amoritas labels survive rather than being regenerated): Pointes North reds, Amoritas "AV" whites, Riesling + Royal Ridge rosé row.
- Graded the gallery interior with ImageMagick only - no AI - so the artists' real work on the walls is untouched.
- Added photos array to the Boathouse entry in src/data/wineries.js, built, pushed, verified live.

**What's live / deployed:**
- https://manitoubeachmichigan.com/wineries - Boathouse card now shows 4 photos
- /images/wineries/boathouse_01..04.jpg (verified image/jpeg, 152-279KB each)
- Commit 2f38719 on main

**Next up:**
- Address discrepancy: wineries.js has the Boathouse at 138 N. Lakeview Blvd; the Amoritas promo card in the tasting room says 132 N. Lakeview Blvd. One of them is wrong - worth confirming with the venue.
- hostedBrands "pours" still reads "Ask what's pouring today". The photos confirm actual SKUs: Pointes North Red Blend, 2021 Riesling, Royal Ridge Blackberry Basil Hard Cider, and the AV white. Could enrich the card and the NOW_POURING_WINES marquee.
- 8 video clips also sit on the OSMO card (~4GB, DJI_..._0001-0009). Unused. Candidate for a wineries page hero or social.

**Notes for other environments:**
- Higgsfield reference-driven relighting preserves real product labels well enough for web use, but the fine label artwork does drift - the watercolor AV monogram is reinterpreted, not copied. Fine at card thumbnail size, visible at full size if you know the original. Never let it generate a real brand's bottle from text alone.
- Higgsfield returned a spurious "ran out of credits" warning at 612 credits remaining and suggested an auto-refill purchase. Ignored it; generation succeeded. Do not act on that upsell without checking balance first.
- Vercel deploy on this repo takes ~40-60s. Polling the URL for HTTP 200 is NOT sufficient - the SPA fallback returns 200 with text/html. Check content-type is image/* before declaring a deploy done.