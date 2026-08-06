## Session: 2026-08-06 ET (update, supersedes earlier entry same day)
**Environment:** Antigravity IDE

**What changed since the first handoff:**
- `ANTHROPIC_API_KEY` is now set in `~/.zshrc` and verified live against the API (HTTP 200, 10 models visible). `~/.zshrc` permissions tightened to 600.
- Timeline spec decided for the Brian - Sylvania edit: **1080p at 29.97**.

**Why 1080p is the right call here:**
- The 123 osmo clips (56% of the shoot) are 1080p60 and become native 1:1, no upscaling.
- The other 95 clips are 4K, which on a 1080 timeline gives 200% punch-in room for free reframes, stabilization and 9:16 reel crops at no quality cost.
- 59.94 osmo conforms 2:1 to 29.97; Avata 100fps gives ~3.3x slow-mo. Only 2 clips (23.98p, in During) don't conform cleanly.

**Still open:**
- The unattended API version of the tagging stage has NOT been written yet. The key is set, but stage 2 of `~/Projects/footage-indexer/` still needs a human to read the review sheets. That build is what unblocks the other 30 customer folders.
- `~/Projects/footage-indexer/` is still local only, not pushed to GitHub.

**Security note:**
- The API key was pasted into the IDE chat, so it lives in this session's local transcript at `~/.claude/projects/-Users-darylyoung/*.jsonl` as well as `~/.zshrc`. Confirmed NOT present in session-handoff.md, CLAUDE.md, the memory files, or the footage-indexer repo, so it has not reached the context repo. Rotate it if a transcript is ever shared off-machine.