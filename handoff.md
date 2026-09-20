## Session: 2026-09-20 ET (continued: live test + blob delete)
**Environment:** Antigravity IDE
**What was done:**
- Yeti ran the live Legacy waitlist test on yetigroove.com/signature#legacy; email + SMS arrived.
- Pulled production env to a gitignored .env.local, listed and deleted the test lead YGL-20260920-Z8F8 with the Vercel CLI, confirmed the store is empty under leads/YGL and the public URL 404s.
- Taught the list/read/delete/list loop; Yeti declined an admin delete button (one-off).

**What's live / deployed:**
- Legacy line on /signature (commit 8eb7bd0), tested end to end. Task board row Done.

**Next up:**
- Vlog pilot clip: the Joe Profit story (Backlog row).

**Notes for other environments:**
- Blob deletes from the Mac: `cd ~/Projects/Yeti-Groove && source .env.local`, `vercel blob list --prefix <path>`, `vercel blob del <full pathname>`.