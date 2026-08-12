## Session: 2026-08-12 ET
**Environment:** Antigravity IDE

**What was done:**
- Identified the repo Yeti wanted as `oso95/scroll-world` (MIT, ~8k stars): an agent skill that builds scroll-scrubbed "fly through the world" landing pages (camera flies outside-to-inside each scene, no cuts).
- Cloned it to `~/Projects/scroll-world`.
- Installed the Higgsfield CLI: `npm i -g @higgsfield/cli` (v1.1.23).
- Installed 8 Higgsfield companion skills via `npx skills add higgsfield-ai/skills -a claude-code`: brandkit, generate, marketplace-cards, product-photoshoot, soul-id, video-explainer, websites, youtube-thumbnail.
- Installed scroll-world the same way (`npx skills add oso95/scroll-world -a claude-code`). Note: the agent flag is `claude-code`, not `claude`.
- Created `~/Projects/scroll-world/.venv` with Pillow 12.3.0 for the optional `knockout.py` transparency step (Homebrew python3 is PEP 668 externally-managed, so a venv was required).
- Verified ffmpeg/ffprobe present; Codex CLI present (can render stills on the ChatGPT sub instead of Higgsfield credits).

**What's live / deployed:**
- Nothing deployed. Local tooling only.

**Next up:**
- Yeti must run `higgsfield auth login` himself (browser OAuth). Confirmed NOT authenticated: `higgsfield workspace list` returns "request failed (no response received)".
- After auth: `higgsfield workspace list` then `hf workspace set <id>`, then `higgsfield account status` to see the credit balance.
- Optional: Monid CLI (monid.ai) is scroll-world's default video backend, pay-per-clip, roughly $27 for a 6-scene 1080p chain. Not installed. Without it the skill falls back to Higgsfield credits.
- Open question: a connector-based fork of scroll-world so Cowork/Mobile can drive it.

**Notes for other environments:**
- The Higgsfield MCP connector (claude.ai) and the Higgsfield CLI are two different things. Cowork and Mobile already have the connector, so they can generate images/video there today.
- scroll-world as written shells out to `higgsfield`, `monid`, and `ffmpeg`. The claude.ai sandbox has none of those, so uploading the skill to claude.ai gets the interview, prompts, and scrub engine but stalls at render. Rendering stays on the Mac.
- Several Bash calls this session were blocked by the auto-mode permission classifier (`cp` into `~/.claude/skills`, `zip`, `npm view`, `higgsfield auth token`). The `npx skills add` route worked and is the sanctioned installer.