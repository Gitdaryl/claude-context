
## Session: 2026-10-15 ET
**Environment:** Antigravity IDE
**What was done:**
- Fingerprinted luckyowlstudio.com (friend Cayt's site): Showit + WordPress blog on BigScoots, not Wix. No API/CLI/MCP exists for Showit.
- Yeti's "padding clashing" screenshots were all in Times New Roman. Headless Playwright render with fonts loaded showed no collisions; blocking Google Fonts reproduced his screenshots exactly. Root cause is a font-blocking browser, not her layout.
- Real issues found: mobile rotated side text clipped off left edge, strikethrough "not ready yet" placeholder live on /weddings, a screenshot PNG used as a content image.

**What's live / deployed:**
- Nothing. Advice only.

**Next up:**
- Yeti to find what blocks fonts.googleapis.com on his Mac (ad blocker / DNS filter).
- Tell Cayt to upload Arapey as a custom font in Showit so the site stops depending on Google Fonts.

**Notes for other environments:**
- Scratch screenshots and overlap scripts were in the IDE scratchpad only; nothing committed.