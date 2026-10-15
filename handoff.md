## Session: Oct 15 2026, 10:20 AM ET
**Environment:** Antigravity IDE
**What was done:**
- YUP Ministries: fixed HeyGen saying "YUP" as "yoop". Yeti confirmed it should be "yup" (uh vowel).
- Tested 5 spellings voice-only (5 credits): "YUP" and "Yuhp" read as "yoop"; "Yup", "yup", "Yupp" read as "yup".
- Created HeyGen brand glossary "YUP Ministries" (b9070af9c24a441188472b94999a6e52), term YUP pronounced "Yup".
- Added brand_glossary_id to every ministry/heygen/render-*.json; README step 2 documents it.
- Verified with a 5s Avatar IV test render of Joe: whisper hears "Yup Ministries" twice (3 credits).

**What's live / deployed:**
- Glossary lives in Yeti's HeyGen account. Nothing published.

**Next up:**
- S6 v1 and v2 renders still say "yoop". Re-render v2 (~100 credits) before sending to Joe, or send as is.
- Credits: HeyGen 1,724 left, resets Nov 10.

**Notes for other environments:**
- Any HeyGen render of Joe must pass brand_glossary_id b9070af9c24a441188472b94999a6e52, or YUP comes out "yoop".