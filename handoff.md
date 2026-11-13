## Session: 2026-11-12 ET
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed the On Point JD Instagram auto-post failures (Nov 10 rj-review-tina, Nov 12 rj-ready-for-winter). Instagram rejected the upload with "Request processing failed" twice each night, an hour apart. Proven not the file, caption, token or quota: the identical request uploaded and reached FINISHED 12 minutes after the last failure (test container, not published).
- Found a second fault the same night: a failed Facebook status read was counted as a failed post, so "Ready for winter" went to Facebook twice (6:00 pm and 7:00 pm).
- Fixed tools/meta-post.mjs: Instagram upload now tries 3 times, 2 minutes apart, with a fresh container; a Facebook status read error no longer exits after the reel is submitted.
- Fixed tools/daily-post.mjs: the log now keeps the Error line instead of the stack tail. Tests pass.

**What's live / deployed:**
- Nothing pushed. Edits are local in ~/Projects/on-point-jd/tools (the launchd job runs from there, so they are in effect).
- Nothing published by Claude: the auto mode classifier blocked the Instagram publish.

**Next up:**
- Yeti: post Ready for winter to IG: `cd ~/Projects/on-point-jd && node tools/meta-post.mjs social/posts/rj-ready-for-winter.json ig`
- Yeti: decide on Tina review reel for IG (same command with rj-review-tina.json), missing since Nov 10.
- Yeti: delete the duplicate Facebook reel https://www.facebook.com/reel/29564479433168628/ (keep 2654445868348748, the one in post-log).
- After posting, add the IG links to social/post-log.json and the content board.

**Notes for other environments:**
- Instagram "Request processing failed" on On Point is a passing Meta-side rejection, not a bad file. Retry later before re-encoding anything.