## Session: 2026-07-14 ET (Receipts, working + commercial plan)
**Environment:** Antigravity IDE
**What was done:**
- Receipts full pipeline VERIFIED working by Yeti on a live presser (transcription + claim cards)
- Added speaker diarization (nova-3, colored SPEAKER labels, attributed claims) and multilingual code-switching (10 languages, claims translated to English)
- Cost lesson: first test burned all $4.39 of console credits in minutes; added wallet guard (25 checks/session, 2 concurrent, queued), downgraded verifier to sonnet, max 2 searches/claim
- Drafted commercial architecture: ~/debate-copilot/COMMERCIAL.md (one-tap Expo app, backend relay holds keys, global claim cache = margin, Stripe web credits to hit ~10% markup, mic + YT-link sources first)

**What's live / deployed:**
- Phase 1 demo artifact (private): https://claude.ai/code/artifact/075f6059-1929-4fe8-930a-1d484c7c080b
- Working local prototype: ~/debate-copilot/prototype/live.html

**Next up:**
- Yeti: add credits at platform.claude.com Plans & Billing before next test
- Decide COMMERCIAL.md open questions (name/domain, consumer vs pro-tool first, transcript retention)
- Phase 1 of commercial build: backend relay (moves keys server-side, adds global claim cache)

**Notes for other environments:**
- Docs: SPEC.md (product) + COMMERCIAL.md (business/mobile) in ~/debate-copilot/
- Cowork could research: receipts.app domain availability, competitor pricing, App Store external-purchase-link rules current state