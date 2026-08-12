## Session: 2026-08-11 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Yeti named the real failure mode: one person posts an event, the other spots a wrong date or spelling, goes in to fix it, and the event isn't on their list at all. My earlier fix only offered to text the other person their own list, which just means "ask her" - not a fix.
- Built shared event lists. Either person can invite the other, and once accepted they both see and edit every event on the business's calendar.
- Two design calls worth remembering:
  1. The link is stored server-side keyed by phone, NOT baked into the magic-link token. Organizers install /my-events to their home screen and the installed launcher freezes its token into start_url, so membership carried in the token would silently never reach the people already using the app.
  2. Sharing requires an invitation accepted on the receiving phone. Email is never verified at submission, so auto-merging by email would let anyone who typed a business's address into the form collect edit links for that business's whole calendar. The invite only goes to a number already on the records and names the inviting number so the recipient can judge it.
- Storage is @vercel/blob in `api/lib/organizer-links.js`, both numbers encoded in the pathname so resolving a group uses list() rather than reading contents (blob content reads are CDN cached and go stale). Blob contents are empty on purpose. A storage failure degrades to solo rather than locking anyone out.

**What's live / deployed:**
- Commit a9db269 on main, deployed and verified.
- Full flow tested on production against a scratch number, then cleaned up: solo before, invite details resolve, forged invite rejected, accept links the pair, both sides then report shared=true, and the partner number (which had submitted nothing) could see the other's event. Test blob deleted and rollback confirmed.
- Gypsy Blue's two numbers each now show the share offer: 9974 sees its 8 and is offered 4607's 10, and vice versa.

**Next up:**
- No SMS in this flow has been watched delivering, because every send target is a client phone. Gypsy Blue will be the first real use.
- No way to un-share yet. Removing someone means deleting their blob under `organizer-links/` by hand.
- Still unfixed: two people editing the same event simultaneously is last-write-wins with no warning (`api/event-edit.js` does a straight PATCH, no version check). More likely now that both can edit everything.
- Three events still unseen from the failed-alert period: two duplicate "Widow and Widower Group" (Review, Jun 10) and "Topless In The Hills" (Pending, May 16).

**Notes for other environments:**
- Event ownership is per phone number. Shared lists are opt-in per pair and live in Vercel Blob under `organizer-links/`.