## Session: 2026-07-07 ET
**Environment:** Antigravity IDE
**What was done:**
- Assessed a YT transcript about "training Opus/Sonnet to think like Fable"; verdict: mostly valid, and Yeti's ~/.claude/fable-playbook.md already covers his "fable mode" five gates
- Flagged that the video's "leaked Fable system prompt" quotes don't match the real Claude Code prompt; treat as unverified, though the extracted behaviors are accurate
- Added rule 11 to fable-playbook.md: "Big model plans, cheap models execute" with a model/effort routing table (Haiku/Sonnet for mechanical + bounded work at low/medium effort, best model for judgment/verification/orchestration at high) and two guard rules (default effort beats max; workers return evidence, not conclusions)
- Updated the playbook one-liner and the matching summary in ~/.claude/CLAUDE.md to stay in sync

**What's live / deployed:**
- Nothing deployed; local config files only

**Next up:**
- Optionally test the routing table on a real multi-agent task to see the cost difference in practice

**Notes for other environments:**
- The fable-playbook now covers orchestration/routing, not just solo discipline. If Cowork or Mobile use subagents, the same rule applies: big model plans, cheap models execute, escalate effort only on failure or high stakes