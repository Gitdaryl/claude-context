## Session: 2026-09-02 ET
**Environment:** Antigravity IDE

**What was done:**
- Diagnosed the Meta 18+ restriction on the Holly & the Yeti Facebook Page. There is no content ratio that lifts it: the Page's own Age Restriction still reads Public, so Meta imposed this by enforcement after ~10 posts were flagged between Jul 21 and Aug 31 (1 in July, 9 in August), and the Page-level gate landed Aug 28.
- Established the scope is narrow. Under-18 only. Adults unaffected, Reels 110,624 views over 90 days, up 512 percent. Talked Yeti out of splitting reach to the YetiGroove Page, which would have diluted a healthy Page to solve a problem he does not have.
- Found the rule the flags actually follow, in Meta's own policy language: they restrict posts "offering to sell alcohol when shared by a legitimate brick-and-mortar business." The trigger is the commercial offer, not the depiction. Tasting-room launches are red; music at a vineyard is green.
- Rewrote the AI Holly persona. The old premise made wine the recurring gag, so every weekly video was a strike candidate by design.
- Found the daily business spotlight was rendering a wine glass for winery and a pint glass for bar, on a daily cron. The bar regex also catches "Bar and Grill", so a family restaurant was rendering a pint glass.

**What's live / deployed:**
- Gitdaryl/Manitou-Beach `4119391`: scripts/holly-persona.md now runs on lake-life sensory envy (cannot feel the water, taste the perch, feel sun or ice) instead of wine envy. Works year round. Adds hard rule 8: alcohol is a fact, never the subject, and that governs the b-roll direction too (no pours, no glass in hand, no bottle hero shots). Pushed roughly ten minutes before the Wednesday 5pm ET cron, so that run used it.
- Gitdaryl/Manitou-Beach `4116a23`: winery icon is now a grape cluster, bar icon is a stool, both verified by render before pushing. Adds docs/ALCOHOL-CONTENT-POLICY.md with the red/amber/green table and the surface routing, plus a pointer in the repo CLAUDE.md.
- Memory: ai-holly-character-voice rewritten, meta-page-age-restriction-holly added.
- Notion: 3 rows on the Master Task Board, 1 row in the Session Brain.

**Next up:**
- Identify what the ~10 flagged posts actually were. Board row, Today.
- Open gap in the diagnosis: the Mac credentials name the Page "Manitou Beach Michigan" (META_PAGE_ID 1049395094924959) but the restricted Page is "Holly & the Yeti". Either it was renamed since May or these are two different Pages. If two, the daily spotlight does not post to the restricted Page and the icon fix does not explain the strikes.
- Confirm whether the Page is in any Facebook Groups. Any age restriction auto-removes it from all of them, which is why "Alcohol-related" stays off the table for now.
- Trash the flagged posts and request review. Window expires around 2026-11-25. Only after the source fix has visibly held.
- Read the first post-change Holly script and check the opener lands without wine.

**Notes for other environments:**
- Do NOT set the Page age restriction to "Alcohol-related". That advice is real but applies to recommendation-suspended Pages, which this is not, and it would remove the Page from every Group it belongs to.
- The editorial rule for anything alcohol-adjacent now lives in the repo at docs/ALCOHOL-CONTENT-POLICY.md. Route red content to the website or the client's own Page, never to Holly's.
- For a winery shoot, cut twice: a wine cut for the client's own Page, an event cut (band, food, people, water) for ours. Reach does not transfer when a client posts, so the client cut adds, it does not replace.