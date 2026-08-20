## Session: Aug 19 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Automated the AI Holly weekend video for Manitou Beach, end to end and verified with real runs.
- Wednesday 8pm ET writes the Thu-Sun script from the PUBLIC /api/events and renders it through HeyGen, then texts Daryl the mp4 and attaches it to the run as a 30-day artifact.
- Posting stays manual: the "AI Holly Post" workflow publishes the exact file he approved and never re-renders, so approving cannot double-charge HeyGen or produce a different take.
- Built v1 with the QA gate in the wrong place, drafting the script and leaving the render manual. Daryl corrected it: he does not want a visitor-facing event rundown texted to him, he wants the finished video. Rebuilt.
- Retired the Thursday slideshow. It had failed silently every week since at least May 28. Cause: the GitHub secret NOTION_TOKEN_EVENTS does not exist on the repo, so it sent an empty bearer token and Notion answered 401. Kept the files, removed only the crons.
- Created ALERT_TOKEN, a low-privilege ops token, so CI can send a text but cannot upload media or publish articles the way ADMIN_SECRET would. ADMIN_SECRET is the master key for a dozen endpoints and is marked sensitive on Vercel, so it cannot be read back anyway.
- Pronunciation fixes live in scripts/holly-pronunciation.json, applied in code to the spoken block only: Manitou to Manitaw, riesling to reesling.

**What's live / deployed:**
- On main: "AI Holly Weekly Video" (cron Wed 8pm ET) and "AI Holly Post" (manual).
- Thursday Roundup and Monday Media Reminder retired, crons removed, files kept.
- ALERT_TOKEN on Vercel Production and in GitHub Actions. HEYGEN_API_KEY in GitHub Actions.
- api/internal-alert.js accepts ALERT_TOKEN or ADMIN_SECRET, so the Sunny Skies dispatcher is unaffected.

**Next up:**
- The Post workflow has never actually published. Exercise it once.
- Scripts run ~106s against an 85-100s target; decide whether to tighten for Reels.
- Decide whether AI Holly ever auto-posts or stays manual forever.
- Local main is behind origin/main; realign with git checkout main && git pull.

**Notes for other environments:**
- HeyGen: AI Holly is avatar 3ff1dbd57555436fb49fd9594a463069 "Holly on Pontoon" with voice a7d9bb2bd0f34fd5a6bcd4b71db2e39f. A stock public voice is ALSO named "Holly" (5d05bed2...), so match on IDs, never names.
- HeyGen v3 rejects a dimension object; vertical is aspect_ratio "9:16" plus resolution "1080p". There is no validate-only mode, so any well-formed probe actually renders and bills.
- TTS is deterministic. A word heard mispronounced once will be wrong every time; it is never a fluke worth waiting out.
- claude-opus-5 and claude-sonnet-5 run adaptive thinking by default and max_tokens caps thinking PLUS response text, so a small budget returns an empty response with no error.
- The checkout in Projects/Manitou-Beach sits on branch seo/crawler-visibility, not main. Scheduled workflows only run from the default branch, so check the branch before assuming a cron is live.