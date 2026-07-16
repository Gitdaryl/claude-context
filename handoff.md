
### Addendum 4 (same session): marquee bug found + fixed
- ROOT CAUSE of "ticker speed never changes" and "restarts at Boot Jack": .marquee-track was viewport-width while content overflowed, so translateX(-50%) looped after half a SCREEN (real speed ~20px/s) instead of half the CONTENT. Fixed with width: max-content on the shared class (also fixes the homepage events ticker's latent seam).
- Real ticker speed now: 376px/s desktop (32s loop, TV-crawl feel), ~109px/s mobile (110s). Verified live in prod bundle (commit 832fba7).