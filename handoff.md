## Session: 2026-10-23 ET
**Environment:** Antigravity IDE
**What was done:**
- YUP Ministries S05 "When Politics Becomes an Idol": applied Joe's Oct 20 email edits, rendered both HeyGen takes, made 6 period B-roll clips + Samuel/Ramah inserts (wide, vertical) + head-bowed prayer, built FULL (4:59) and REEL (1:17), thumbnail, reel cover, YouTube copy. All in ~/Documents/Joe-Profit/ministry/Sessions/S05 When Politics Becomes an Idol/
- S01 fix Joe flagged: at 3:46-3:54 the teammates were Black (Joe was the only Black player). New field clip, S01 FULL + REEL re-rendered; old cuts in Older versions.
- HeyGen: plan premium credits were down to 53, so takes now bill the $100 API wallet via HEYGEN_API_KEY (key in ~/.config/heygen-api-key). Measured ~$7.19/min; $40.45 spent, $53.80 left.
- Kit: new kie-gen.py, check-take.py; build.mjs fix for 2-frame reframes between back-to-back cards.

**What's live / deployed:**
- Nothing uploaded. S01-S05 are ready to upload (Yeti uploads; S01 must be the Oct 23 re-render).

**Next up:**
- Yeti: upload S01 (new cut), S02, S03, S04, S05 to the Joe Profit channel playlist.
- S06 redo on Avatar V (script to Joe first). Wallet $53.80 covers roughly one more episode's takes; plan credits reset Nov 10.
- Kie balance check before S06 inserts; Higgsfield ~1-2 credits left.

**Notes for other environments:**
- Never run `heygen auth login`; it would wipe the OAuth plan login. Use the HEYGEN_API_KEY env var per command.