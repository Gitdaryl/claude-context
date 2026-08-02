## Session: Aug 2, 2026 ET (checklist UX fix)
**Environment:** Antigravity IDE
**What was done:**
- Fixed two Idea Greenhouse checklist quirks Yeti reported:
- Scroll jump: every checkbox click re-rendered the board and reset column scroll to top. render() now saves and restores the board's horizontal scroll and each column's vertical scroll. Verified live with a scripted Playwright test (scrollTop 1564 before and after click).
- Checkbox semantics: checked items no longer strikethrough (read as "idea eliminated"). They dim, keep their text readable, and sink below the open items, so the remaining work is always on top. Cards now show a progress pill (☑ 2/5, turns green when complete). SOP logic: a checklist is a work queue, checked = progress banked, not elimination.
- Test clicks toggled 3 real to-dos during verification; all restored to original state via API, board verified clean.

**What's live / deployed:**
- idea-greenhouse-pi.vercel.app, commit a204e2d on Gitdaryl/idea-greenhouse main. (Deploy note: index.html deployed via vercel --prod BEFORE the git commit this time; commit pushed after, content identical.)

**Next up:**
- Optional: date field in the Plant It add bar for one-step committed entries.

**Notes for other environments:**
- Nothing new to configure. UI behavior change only.