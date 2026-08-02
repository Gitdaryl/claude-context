## Session: Aug 2, 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Added "On the Hook" commitments layer to Idea Greenhouse. Problem solved: committed shoots (business spotlights etc.) were getting lost among incubating ideas, dates approaching with no plan, and filmed footage sitting in camera forgotten.
- New card fields: `committed` (bool) and `due` (YYYY-MM-DD), validated server-side. Setting a due date auto-commits; uncommitting clears the date.
- New 🔥 On the Hook strip above the board: committed unreleased cards sorted by urgency. Overdue = red, 5 days or less = amber, committed cards in Editing = purple "in the can · needs edit", undated last. Tapping a row scrolls to and flashes the card.
- Cards got: 🔒 Commit/Uncommit button, committed pill, urgency-colored date pill, in-the-can pill, and a Shoot/due date picker.
- Verified live with Playwright screenshots (desktop + mobile), test cards cleaned up after.

**What's live / deployed:**
- idea-greenhouse-pi.vercel.app, deployed via Vercel CLI, pushed to Gitdaryl/idea-greenhouse main (commit b810d7e).

**Next up:**
- Optional: make Grow aware of committed status (research a shoot plan vs. incubate an idea).
- Optional: could add a date to the Plant It add bar for one-step committed entries.

**Notes for other environments:**
- Workflow for Yeti: when you agree to film something, plant the card and hit 🔒 Commit + set the shoot date. After filming, drag it to Editing; it will sit in On the Hook as "in the can" until edited. Nothing committed can silently rot anymore.