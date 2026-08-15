## Session: Aug 14, 2026 ET (activity feed + notifications)
**Environment:** Antigravity IDE
**What was done:**
- Idea Greenhouse: built the notification layer Yeti asked for (know when Holly adds/moves things).
- Activity log: every mutation writes a one-blob-per-event record (planted, moved, harvested, committed, dated, checked-off, grew, deleted) with the acting person stamped and validated. GET/DELETE /api/activity, auto-prune at 45 days.
- Bell in the header with a red unread count of the OTHER person's actions since last viewed (per-device lastSeen in localStorage). Tapping opens a feed ("Holly moved 'X' · germinate → editing · 2h ago", names color-coded, unseen rows highlighted) and clears the badge. Refreshes on load, on tab focus, and every 2 minutes.
- SMS seam: if NOTIFY_WEBHOOK env var is set on Vercel, every event also POSTs there after the blob persists (persist-before-notify). Intended target: an n8n webhook that texts. n8n connector not authorized in this session, so wiring SMS is pending Yeti authorizing it in claude.ai connector settings or providing a webhook URL.
- Verified end to end live: Holly-actor API actions produced badge count 2 for Yeti, feed rendered, badge cleared on view. All test cards and test activity events deleted after.

**What's live / deployed:**
- idea-greenhouse-pi.vercel.app, commit 0f9c0e1 on Gitdaryl/idea-greenhouse main.

**Next up:**
- SMS: set NOTIFY_WEBHOOK on the Vercel project to an n8n webhook that sends texts (needs n8n auth or URL from Yeti).
- Optional: Plant It date field; my-tasks filter.

**Notes for other environments:**
- Noticed a real card in Editing showing "in the can · needs edit · 10d late" on the hook strip, so the system is being used with real work.