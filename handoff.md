## Session: 2026-08-15 ET (continued)
**Environment:** Antigravity IDE

**What was done:**
- Fixed the Manitou Beach search corpus, which had been empty for over a week while every signal reported healthy. Root cause chain: GEMINI_API_KEY was absent until 2026-08-14, then present but every embedding call failed. The pinned model (text-embedding-004) is the strong hypothesis, unverified because the key is marked sensitive in Vercel and will not pull.
- Made the cause moot rather than guessing: embeddings.js no longer pins a model. Candidates are tried in order (GEMINI_EMBED_MODEL override, gemini-embedding-001, text-embedding-004), first that answers is remembered. Tested against a mock: falls back on 404, does NOT walk the list on 429.
- Real Google errors now propagate instead of the string "embedding failed", which is what made this undiagnosable from outside.
- Shards are tagged with the model that built them and a mismatched shard is ignored until reindex. Scoring 001 queries against 004 documents returns confident nonsense.
- cron-reindex now returns 500 when it indexes zero passages. It was returning 200, which is why the Vercel cron dashboard showed a green tick every night.
- Correction to an earlier claim in this session: the heartbeat infrastructure ALREADY existed and is well built (lib/cronHeartbeat.js, hooked through lib/cronAuth.js so all crons get it free, read by /api/status-agents). No 17-file edit was needed. What was actually missing: it records INVOCATION not outcome, and cron-reindex was not in the JOBS table at all. The one job nobody watched was the one that broke.
- Added recordResult/readResults, moved the job registry to lib/cronJobs.js so status-agents and the watchdog share one list, and built api/cron-watchdog.js (daily 11:00 UTC). It checks outcomes and facts, not tick-boxes: corpus passages above zero, sources not failing, rebuild within 48h, jobs late or reporting failure. Texts Daryl and returns 500. Refuses to report all-clear when it cannot read the heartbeat store.
- WongDoody application: the page claimed 18 / eighteen / nineteen agents in prose while the live widget it fetches reported 20, on a page whose whole claim is "this reads live, it isn't typed in". Counts are now injected by the same fetch that draws the widget, so they cannot drift again. Endpoints corrected 173 to 166.
- Widget now reports health rather than attendance, amber when degraded. Yeti chose the honest option deliberately: a dashboard that can only show green is indistinguishable from a hardcoded one.
- Pillar 5 quoted their "vector search" requirement and did not answer it. It now does, using the real retrieval layer. Cover letter (both .txt and .md) gained a fifth item on retrieval plus the monitoring lesson. Pillar map upgraded from "Strong except vector search" to "Strong". Checklist item ticked, with interview depth notes added (256 dims is Matryoshka truncation, pre-normalised vectors, separate query/document task types, per-source shards).

**What's live / deployed:**
- Manitou Beach: DEPLOYED and confirmed on manitoubeachmichigan.com. /api/status-agents returns 20 agents with the new health and outcome fields, cron-reindex and cron-watchdog both in the registry.
- nas-backup: INSTALLED. All four launchd jobs loaded, sentinel created, targets.json filled with 4 blob stores. First real snapshot ran: 325 objects, 331MB on the NAS, restore drill passed on yeti-groove.
- yeti-positioning: edited but NOT deployed. Needs `vercel --prod` from ~/Projects/yeti-positioning.

**Next up:**
- TRIGGER THE REINDEX. Vercel dashboard, Settings, Cron Jobs, Run now on /api/cron-reindex. Then `curl -s https://manitoubeachmichigan.com/api/retrieve | jq .status.passages` must be above zero.
- DO NOT SEND the WongDoody letter while passages reads 0. The page and letter both now claim vector search is live.
- Deploy yeti-positioning.
- Upstash creds for nas-backup must come from the Upstash console, not `vercel env pull` (Vercel returns integration vars as empty strings).
- Point Time Machine at a NAS share in UGOS Pro and set a size cap. It currently has no off-disk destination at all.
- Optional: hide the Manitou voice concierge mic button when the ElevenLabs session fails to start. Currently it renders a dead button.

**Notes for other environments:**
- nas-backup repo not yet pushed to GitHub.
- NAS sleeps 23:30 to 09:00 weekdays, 10:00 weekends. Any scheduled job touching 10.10.10.2 must live inside that window. n8n on the VPS cannot reach it (private LAN address, would need Tailscale).
- Hardlinks do not work over that SMB share. Tested. Anything doing snapshot-style backup there must use content addressing, not --link-dest.