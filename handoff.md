## Session: 2026-08-15 ET
**Environment:** Antigravity IDE

**What was done:**
- Answered an AI-bubble exposure question, then audited the live projects for real operational risk. Result: no hotlinked vendor CDN assets anywhere (the thing most likely to break), photo pre-screen already fails open, vendor spread across Anthropic/Gemini/ElevenLabs is sane.
- Two genuine gaps found: 17 Manitou-Beach cron endpoints only `console.error` on failure, so a vendor repricing would stop the agents silently; and `VoiceConcierge.jsx` has no fallback if ElevenLabs is unavailable (visitor gets a dead mic button).
- Discovered Time Machine has NO off-disk destination. `tmutil destinationinfo` = Kind: Local, `tmutil latestbackup` empty, target resolves to the internal 2TB SSD which is 93% full. Local APFS snapshots only.
- Built ~/Projects/nas-backup: backs up Vercel Blob + Upstash KV + git mirrors to the UGREEN DXP6800 Pro (10.10.10.2, 73TB, 50TB free), scheduled around the NAS sleeping 23:30-09:00 weekdays / 10:00 weekends.
- Key discovery mid-build: hardlinks FAIL over this SMB share (tested, not assumed). The standard dated-tree + `--link-dest` design would have silently written a full 279MB copy every week. Switched to a content-addressed object store + JSON manifests, which needs no hardlinks.
- Also added: TM pause at 22:45 / resume after wake, because TM over SMB to a sleeping NAS can corrupt the sparsebundle.

**What's live / deployed:**
- Nothing deployed. nas-backup is built and tested but NOT installed (install.sh not run, no launchd jobs loaded).
- Verified against the live Manitou Beach store and the real NAS share: cold pull 279MB/20s, warm pull reused all 240 objects in 1.3s, restore byte-identical to live blob (cmp), GC collects orphans correctly.

**Next up:**
- Yeti runs `./install.sh`, sets the TM destination in UGOS Pro, fills targets.json.
- Upstash creds must come from the Upstash console, not `vercel env pull` (Vercel returns sensitive integration vars as empty strings).
- NOT DONE: the cron heartbeat + watchdog for Manitou-Beach's 17 cron endpoints. Needs a `api/lib/heartbeat.js` plus a one-line beat call in each handler. Deferred because it touches production cron handlers and deserves its own pass.
- Optional: hide the voice concierge mic button when the ElevenLabs session fails to start.

**Notes for other environments:**
- nas-backup repo not yet pushed to GitHub.
- The NAS sleep window (23:30 to 09:00/10:00) constrains any future scheduled job touching 10.10.10.2. n8n on the VPS cannot reach it: private LAN address, would need Tailscale.