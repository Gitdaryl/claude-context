## Session: 2026-08-27 ET
**Environment:** Antigravity IDE

**What was done:**
- Ran the AI Holly reel kit on this week's HeyGen render (~/Downloads/83c5f414542d42ec80ebc2088f2559b0.mp4) for the AUG 27-30 weekend. 8 events anchored, none dropped, contrast passes WCAG AA.
- Fixed a real bug in holly-reel-kit/reel/run.mjs: arg() returned argv[0] (the node binary path) for any absent flag, because indexOf is -1 and -1 + 1 is 0. --thursday was therefore never optional and the run crashed with "Invalid time value".
- Fixed a layout error that blocked the render: Poppins ink at 62px ran ~3px past the title's line box and the clamp's overflow:hidden was shaving descenders. Added 4px vertical padding to .beat-what .title in build.mjs rather than changing the type.
- Fixed silent SMS failure in run.mjs: it only checked msg.error_message (delivery failures) and not msg.message (API errors), so a 401 printed "401, undefined segments" and then "Done."
- Verified the render by extracting frames, not by trusting the check.

**What's live / deployed:**
- Uploaded to Blob preview: https://dmg0joh3jdjfmu8k.public.blob.vercel-storage.com/holly-weekend/preview/holly-2026-08-27-overlaid.mp4
- Local master: ~/Projects/holly-reel-kit/holly-2026-08-27-OVERLAID.mp4 (172 MB), delivery copy -OVERLAID-web.mp4 (88 MB)
- NOT posted. NOT published to the --post path (that needs `node run.mjs --video=<file> --publish`).

**Next up:**
- THE TEXT TO HOLLY DID NOT SEND. Manitou-Beach/.env has no TWILIO_* vars at all, only UNSPLASH_ACCESS_KEY and BLOB_READ_WRITE_TOKEN, so run.mjs POSTed to /Accounts/undefined and got 401. Either add the three TWILIO vars from the Twilio console, or add a `to` parameter to /api/internal-alert (which currently only texts ADMIN_PHONE). Board row filed.
- FLYTE at Devils Lake Bar & Grill (Sat Aug 29) has no start time in the events DB, so the reel shows TIME TBA. Board row filed. Write it to Time End with an EN DASH.
- The .spoken.md sidecar item from last week is still open; it matters less now that captions are off by default.

**Notes for other environments:**
- The weekly command is: nvm use 22; cd ~/Projects/holly-reel-kit/reel; node run.mjs --video=<file>. Add --keep-transcript when only the look changed. --upload and --notify are opt-in.
- Twilio credentials live only on Vercel for this project, not on the Mac. Any local script that texts will fail the same way.