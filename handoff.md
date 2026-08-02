## Session: Aug 2, 2026 ET (nav + assignees + urgency)
**Environment:** Antigravity IDE
**What was done:**
- Idea Greenhouse round 4, from Yeti's feedback:
- Horizontal scroll fix: Yeti could not scroll right with a mouse (Mac hides scrollbars, wheel gets captured by columns). Added ‹ › arrows in the header that move one column per click, plus an always-visible styled scrollbar under the board. Scroll snap relaxed from mandatory to proximity. First attempt used floating edge arrows but they covered checkboxes, moved to header.
- Per-task assignees like Trello: every checklist item has a chip that cycles + → Yeti → Holly → off. Colored to match author tags (blue Yeti, pink Holly). Stored as who on each checklist item, validated server-side.
- Staleness jolt: cards stuck 30+ days get a red 🥀 wilting tag and a slow pulsing red border. Committed cards past their due date pulse too. The 14-day amber "stuck" tag remains the first warning tier.
- All verified live with Playwright (arrows scroll 14 → 608, chip cycles Yeti and back to +), test assignment reverted, board clean.

**What's live / deployed:**
- idea-greenhouse-pi.vercel.app, commit 53a021b on Gitdaryl/idea-greenhouse main.

**Next up:**
- Optional: date field in the Plant It add bar.
- Optional: "my tasks" filter showing only items assigned to the signed-in person.

**Notes for other environments:**
- Desktop users: header arrows, visible scrollbar, shift+mousewheel, or trackpad swipe all scroll the board now. Mobile swipes as before.