## Session: 17 Aug 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Found all 77 Chateau Aeronautique events on the Manitou Beach site were published as free. Root cause: `scripts/import-chateau-events.mjs` never set `Cost`, and a blank Cost renders no badge and sets `isAccessibleForFree: true` in the Event schema.
- Backfilled `$25 cover` on all 77 rows in Notion via a new reusable `scripts/set-chateau-cost.mjs`, and patched the importer so it can never happen again.
- Reconciled the venue's conflicting data. Address was 1849 E Parnall Rd, Jackson; correct is 12000 Pentecost Hwy, Onsted, which moved the map pin about 22 miles. Phone 795-3620 retired for 446-4052. Dead domain `chateauaeronautique.com` link replaced. Added the winery to SITE_KNOWLEDGE, it was missing.
- Audited the venue's own web presence for a sales meeting and built a one-page leave-behind PDF.

**What's live / deployed:**
- Manitou Beach commit `6e040a1` pushed to main, Vercel production Ready, verified in the served bundle (not just a 200).
- All 37 upcoming Chateau events on `/api/events` carry the $25 cover.
- Community POI row for the winery patched live in Notion (address, coords, phone, website).

**Next up:**
- Paste the updated prompt from `agent_configs/PASTE-INTO-ELEVENLABS-PROMPT.txt` into the ElevenLabs dashboard. Until then the voice concierge still gives the Jackson address.
- Meeting with Jerry, the GM, no date set. Leave-behind is on the Desktop as `Chateau-Aeronautique-Findings-YetiGroove.pdf`, source in `~/Projects/chateau-aeronautique/`.
- Get one number from Jerry before quoting: average paid heads per show.
- Unrelated in-progress work left uncommitted in the repo: cron watchdog, corpus, embeddings, `vercel.json`.

**Notes for other environments:**
- Canonical venue name is Chateau Aeronautique Winery. `chateauaeronautique.com` is unregistered; Jerry should buy it, we should not.
- Session Brain row could not be written, the Notion connector disconnected mid-session and needs re-authorising in claude.ai connector settings.