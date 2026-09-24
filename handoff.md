
## Session: 2026-09-24 ET
**Environment:** Antigravity IDE
**What was done:**
- UI/UX review of manitoubeachmichigan.com (desktop + phone, headless screenshots + DOM audit)
- Found broken logos: Holly, Blackbird Cafe, Gypsy Blue. Cause: WebP sweep commit 8649917 deleted 142 originals; logo URLs live in Notion, not code, and SPA fallback returns HTML 200
- Drafted fix: vercel.json rewrite legacy /images/*.png|jpg -> .webp. Committed in a clean clone (scratchpad mbclean), push BLOCKED by permission guard, NOT live

**What's live / deployed:**
- Nothing

**Next up:**
- Push the vercel.json rewrite (or add it by hand) and re-check the 3 logos
- Design pass: 12px text floor -> 16px, tap-to-call on all 32 phone numbers (only 3 are links), hide public "Upgrade" labels, fix duplicate Cherry Creek Cellars, replace night-campfire hero frame, unique Dispatch cover images

**Notes for other environments:**
- Local ~/Projects/Manitou-Beach is 3+ commits behind with uncommitted edits (App.jsx, offers.js, robots.txt, promo-claim.js deleted) from another machine. Don't commit over it.