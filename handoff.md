## Session: Aug 19-20 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Built and shipped the AI Holly weekly video automation for Manitou Beach, verified with real runs end to end.
- Wednesday 8pm ET now writes the Thu-Sun script from the PUBLIC /api/events, renders it through HeyGen, texts Daryl the mp4, and attaches it to the run as a 30-day artifact. Posting to Facebook and Instagram is the only manual step.
- Built it wrong first: v1 drafted the script Wednesday and left rendering as the approval. Daryl said a visitor-facing event rundown texted to him was useless, he wants the finished video and the gate belongs on posting. Rebuilt.
- Retired the Thursday slideshow and its Monday reminder (crons stripped, files kept). It had failed every week since at least May 28 because the GitHub secret NOTION_TOKEN_EVENTS does not exist on the repo, so it sent an empty bearer token. Twelve silent failures.
- Created ALERT_TOKEN, a lower-privilege ops token, so CI can text but cannot upload media or publish articles the way ADMIN_SECRET would. ADMIN_SECRET is marked sensitive on Vercel and cannot be read back.
- Backfilled times on ALL 37 upcoming Chateau Aeronautique shows, 8 to 11 PM. Feed-wide, events with no start time went from 44 of 70 down to 7.
- Fixed pronunciation: Manitou now says "Manitaw", riesling says "reesling". Applied in code to the spoken block only.
- Rewrote the persona so she talks like a person: contractions everywhere, and she no longer announces "I am AI Holly" at camera. Also widened rule 1 to ban invented opinions after a draft praised a band she has never heard.

**What's live / deployed:**
- On main: "AI Holly Weekly Video" (cron 0 0 * * 4 = Wed 8pm ET) and "AI Holly Post" (manual, posts the existing Blob video, never re-renders).
- Thursday Roundup and Monday Media Reminder retired, crons removed, files kept for a redesign.
- ALERT_TOKEN and HEYGEN_API_KEY in GitHub Actions; ALERT_TOKEN on Vercel Production.
- All 37 Chateau events now carry 8:00 PM to 11:00 PM.
- HeyGen wallet was $97.23 before roughly four full renders plus two test clips.

**Next up:**
- The Post workflow has NEVER actually published. Exercise it once on a week he is happy with.
- Local main is behind origin/main. The checkout sits on branch seo/crawler-visibility, not main.
- "Johnny & Lighting The Storm Bandits" at Devils Lake Bar & Grill: still no start time, and "Lighting" is probably a typo for "Lightning". Both live in the events data.
- Decide whether AI Holly ever auto-posts or stays manual forever.
- Rebuild the Thursday slideshow with a new design (own board row). Re-sync or drop NOTION_TOKEN_EVENTS first and add a failure alert before giving it a cron.

**Notes for other environments:**
- HeyGen: AI Holly is avatar 3ff1dbd57555436fb49fd9594a463069 "Holly on Pontoon" with voice a7d9bb2bd0f34fd5a6bcd4b71db2e39f. A stock public voice is ALSO named "Holly" (5d05bed2...), so match on IDs, never names.
- HeyGen v3 rejects a dimension object; vertical is aspect_ratio "9:16" plus resolution "1080p". There is no validate-only mode, so any well-formed probe actually renders and bills.
- Manitou events DB: the property named Time is a read-only created_time system field. Real times live in Time End as one string split on an EN DASH. A hyphen makes the whole string become the start time.
- TTS is deterministic. A word heard mispronounced once is wrong every time, never a fluke.
- A prompt teaches by its own register. The Holly scripts were robotic partly because the persona file itself was written in expanded form; write instruction files in the voice you want back.
- claude-opus-5 and claude-sonnet-5 run adaptive thinking by default and max_tokens caps thinking PLUS response text, so a small budget returns an empty response with no error.
- Scheduled workflows only run from the default branch. Check the branch before assuming a cron is live.