## Session: 2026-06-11 (AEST)
**Environment:** Antigravity IDE

**What was done:**
- Analyzed HeyGen's new credit-based pricing (replaces old "unlimited"). Key: Avatar V/IV burn 20 credits/min; standard avatars ~1/min. API rule ~$3/min for Avatar V ($0.05/sec).
- REVIVED YetiClone. The project was shelved 2026-04-13 because Avatar V had no API and v2 Avatar IV gave floating-teeth output. Avatar V API shipped May 2026 - re-validated live with Daryl's account: 10/10 generations clean, 0 failures, frame-checked, teeth-gate FIXED. Both original blockers are dead.
- Migrated generate endpoint v2 -> v3 (engine.type avatar_v, orientation->aspect_ratio). Commit 36e4221.
- Built the shared backend + missing product pieces (commit 45f0c33): Vercel Blob JSON DB (replaces localStorage so client + admin share state), "your video is ready" delivery email (was promised, never built), hybrid QA (new clients gated for first N videos then auto-flip to self-serve), regen loop (backs both client "Request changes" and admin "Flag for Edit"), HeyGen completion webhook. Rewired AdminQueue/VideoLibrary/CreateVideo/Dashboard off localStorage. Build passes.
- UX direction set: all 9:16 vertical, client controls = 3 only (change outfit / regenerate / approve), consolidate the two video-creation doors into one wizard, separate client vs admin nav. Positioning = sell ACCOUNTABILITY not "I hand-make each video" (human-in-the-loop QA is real via gating, not theater).
- Billing: insurance client (Sam Quisenberry, State Farm) is 2 months in, NO invoices sent. Drafted catch-up invoices YC-1001 ($320 May) + YC-1002 ($320 June) = $640, ready to paste into Novo. 10 videos delivered, first 2 free (onboarding bonus), June subtitles comped as a trial - both shown as visible $0 gift lines.
- Locked in "First 2 Free" acquisition SOP (memory: feedback_first_two_free_sop) - per client AND per agent, framed as a bonus never "free".

**What's live / deployed:**
- Code pushed to github Gitdaryl/YetiClone main (36e4221, 45f0c33). Build passes.
- NOT deployed-functional yet: portal is INERT until Vercel env is set (esp. a Blob store for BLOB_READ_WRITE_TOKEN). Nothing runs without it.

**Next up (added to Command Center):**
1. GO LIVE - create Vercel Blob store + set env (HEYGEN_API_KEY validated today, voice/avatar defaults, RESEND_API_KEY). Unlocks self-serve AND auto-billing. Claude can do it with go-ahead. [Status: Today]
2. Consolidate client UI into single wizard (Sonnet).
3. Org/account layer before the 3 other agents onboard (month 3 = now-ish) - one consolidated invoice to the owner.
4. Monthly billing assistant (per-video auto-reminder reading the delivery log) - depends on go-live.
5. Subtitle engagement result from marketing agent -> if positive, bump Hyperframes caption automation up the queue.

**Notes for other environments:**
- ACTION FOR DARYL: send Novo invoices YC-1001 + YC-1002 ($640 total) - 2 months of uncollected revenue.
- HeyGen API key was pasted in plaintext in the IDE session - consider rotating after, Daryl's call.
- "First 2 free" is now standard policy across Yeti Groove Media client acquisition, not just YetiClone.
- Daryl flagged ADHD/overload - lots of projects, forgets what needs attention. The Command Center task list is the externalized memory; keep adding tasks proactively so nothing relies on him remembering.