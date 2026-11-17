
## Session: 2026-11-16 (evening ET)
**Environment:** Antigravity IDE
**What was done:**
- Devon reported OnPoint Facebook reels show a notification but "This content isn't available"; friends see the same. Diagnosed: Graph API reports all 14 reels published and Public, FB views 0 to 8 per reel over 10 days, anonymous fetch of every OnPoint permalink hidden while the same fetch of Manitou Beach reels renders. Cause: OnPoint Poster Meta app (1609599310715590) still in Development mode, so only Daryl (app role) can see what it posts. Instagram and YouTube unaffected.
- Nov 16 daily post: FB + YT went out (Shields Up); IG rejected the upload twice with the recurring rupload ProcessingFailedError.
- Filed two Today rows on the Master Task Board; memory updated (onpoint-posting-tools, new meta-dev-mode-hides-page-posts).

**What's live / deployed:**
- Nothing deployed. No code changed.

**Next up:**
- Yeti: developers.facebook.com > OnPoint Poster > App settings > Basic > Privacy Policy URL https://onpointjd.com/privacy > Save, then flip App Mode to Live. Before 6 pm ET Nov 17 so the daily post is the test.
- Yeti: `cd ~/Projects/on-point-jd && node tools/meta-post.mjs social/posts/shields-up.json ig`
- Claude after the flip: anonymous curl of facebook.com/reel/1700412288386467 must show og:title; check whether old reels became visible or need re-publishing; read the Nov 17 post log at 6:05 pm.

**Notes for other environments:**
- Do not tell Devon the reels are fine; they are not visible to anyone but Daryl until the app goes Live. Add "switch app to Live + anonymous curl with control" to every Meta posting setup.