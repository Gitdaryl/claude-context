
## Session: Oct 14 2026 (evening ET), continued
**Environment:** Antigravity IDE
**What was done:**
- Walked Yeti through Meta setup click by click (guide + all ids: on-point-jd/social/META-SETUP.md). Portfolio On Point JD Roofing 1851270032966151, ad account OnPoint JD Ads 2096465794304438 (Yeti's card), dataset/Pixel 1084662177881561, CAPI token generated (business email was the missing prerequisite), test code TEST44463.
- Yeti set META_PIXEL_ID, META_CAPI_TOKEN, META_TEST_EVENT_CODE on both Vercel projects.
- Pushed on-point-jd 299a3ab (pixel + Lead/Contact CAPI, docs) and onpoint-office ac075b5 (meta-sync cron, meta_events migration). Office commit excluded another session's uncommitted work.
- Verified live: onpointjd.com/api/pixel serves the pixel with the id (200, application/javascript); headless load sets _fbp and builds _fbc from fbclid, keeps it in sessionStorage, a call tap posts /api/track; app.onpointjd.com/api/meta-sync answers 401 without bearer, 405 on POST.
- webp sweep on on-point-jd walked 1,186 untracked social/ images for 6 min; killed, no damage; memory updated (scope it to site/).

**What's live / deployed:**
- Both deploys live. meta_events migration NOT pushed (no supabase CLI on PATH; Yeti runs npx supabase db push). Until then the hourly meta-sync logs an error per run; harmless.

**Next up:**
- Yeti: npx supabase db push (office); domain verify onpointjd.com in Meta (TXT on Vercel DNS); watch Events Manager > Test events, then vercel env rm META_TEST_EVENT_CODE on both + redeploy.
- Board rows: "Meta access for Daryl" closed Done; "first Meta ad spend DECIDE funding model" carries the open list.