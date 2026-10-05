
## Session: 2026-10-05 ET
**Environment:** Antigravity IDE
**What was done:**
- Reviewed the OnPoint /estimate calculator (math sane; several rates still guessed, listed in CONFIRM.md)
- Talked Yeti out of a rigged spin wheel; built the honest version instead: guaranteed $1,000 off for booking a free inspection + one bonus spin (server picks by weight, slices drawn at real odds), countdown to a real end date, 60s engaged-time trigger (inline card, no popup)
- One code per property address, ZIP-gated, insurance jobs excluded; claims go through api/lead.js (persist before notify)
- /desk page (PIN) to edit amount, end date, bonuses, ZIPs, and see the funnel (shown, opened, spun, booked)
- Tested headless (phone + desktop) and end-to-end against the real Blob store; test blobs deleted

**What's live / deployed:**
- Nothing. All changes are uncommitted in ~/Projects/on-point-jd (short links /price /fb /ig /gp already point at /estimate, so deploying = public)

**Next up:**
- Jay/Devon OK the offer terms (CONFIRM.md: bonus list + costs, $8k min job, 60-day signing, Oct 31 end, ZIPs)
- Yeti: vercel env add OFFER_DESK_PIN production (in site/), then commit-push
- Michigan: a team member has a MI residential builder license; attorney check before MI returns (the company itself likely needs the license)
- Twilio not configured on onpointjd (no customer texts); Meta Pixel row still waiting

**Notes for other environments:**
- Offer settings live in Vercel Blob (offer/config/), edited at onpointjd.com/desk, not Notion