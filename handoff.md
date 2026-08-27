## Session: 2026-08-27 ET
**Environment:** Antigravity IDE

**What was done:**
- Overlaid the AI Holly reel for AUG 27-30, then automated the whole graphics pass, then did a full redo when Cherry Creek landed three new listings.
- AUTOMATION: second job on the Wednesday workflow runs the overlay on the Mac Studio via a self-hosted GitHub runner, chained to the render job. Verified by real runs. Added overlay_only so graphics can be redone without re-billing HeyGen, and a watchdog job on GitHub hardware because the overlay's own failure alert runs on the Mac.
- SEND: routed through /api/internal-alert with named recipients (admin default, holly from HOLLY_PHONE) instead of Twilio direct, which never had credentials anywhere. Gated: Holly only gets it when the reel is clean, otherwise Daryl gets it with the reason.
- SCRIPT: strict chronological order, the jealousy aside freed from the opener onto any distinctive event, "in the evening" for a missing time, and she no longer reads street addresses.
- GRAPHICS: spine tapers to a faded point, cards end on her own pause with bare video between topics, closing URL card, colour-bearing logos fill the circle (measured with ffmpeg, not hand listed), whooshes on card in/out.
- BUGS FIXED: arg() returned argv[0] for absent flags; Poppins ink overran the title clamp; SMS failures printed "Done."; job-level PATH would have hidden node; events feed had no cache buster; cost badge said FREE for "free for members / $10"; dateEnd holding a season end spread events across every day.
- DATA: all three Cherry Creek rows had a street address in Location instead of the venue name, in two spellings. Fixed, so their logo matches and their events anchor.

**What's live / deployed:**
- Gitdaryl/Manitou-Beach main. Runner "yeti-mac-studio" online. HOLLY_PHONE on Vercel Production.
- Latest reel rendered and held back correctly: https://dmg0joh3jdjfmu8k.public.blob.vercel-storage.com/holly-weekend/preview/holly-2026-08-27-overlaid.mp4
- NOT sent to Holly. NOT posted.
- holly-reel-kit is a local git repo, still no remote.

**Next up:**
- BLOCKING THE RE-RENDER: confirm with Cherry Creek whether Vineyard Jams runs Sunday, whether to promote 6 PM doors or 7 PM music, and whether Acoustic Sundays is free. Confirm Frankly Jack is 4 PM not 7 PM (three rows describe 4-7 PM while the Time field says 7:00 PM). Both filed as Today.
- Then ONE HeyGen render fixes everything and the reel should auto-send.
- Auto-login still off, so a power cut with nobody home queues the Wednesday job.
- Push holly-reel-kit somewhere.

**Notes for other environments:**
- Redo graphics without a new HeyGen charge: Actions > AI Holly Weekly Video > Run workflow > overlay_only=true, week=YYYY-MM-DD.
- Twilio credentials exist ONLY on Vercel. Anything that texts must go via /api/internal-alert.
- In the events DB, dateEnd is sometimes a season end rather than an event end. Do not assume it spans days.