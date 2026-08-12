## Session: 2026-08-12 ET
**Environment:** Antigravity IDE

**What was done:**
- Identified the repo Yeti wanted as `oso95/scroll-world` (MIT, ~8k stars): an agent skill that builds scroll-scrubbed "fly through the world" landing pages (camera flies outside-to-inside each scene, no cuts). He first asked for it as "scrollable", which does not exist as a Claude tool.
- Cloned it to `~/Projects/scroll-world`.
- Installed the Higgsfield CLI: `npm i -g @higgsfield/cli` (v1.1.23, aliases `hf` and `higgs`).
- Yeti authenticated via `higgsfield auth login` (browser OAuth, he ran it).
- Selected the workspace: "Private" `5d35139d-6457-4a9d-b5e4-ad3036bacab1`, ultimate plan. `higgsfield account status` errors with "No workspace selected" until you run `hf workspace set <id>`, which the official install instructions omit.
- Verified end to end: account status returns admin@yetigroove.com, ultimate plan, **345.11 credits**. `higgsfield model list --video` returns the full catalog (Seedance 2.0 / 2.5 / Mini, Kling 3.0, Veo 3.1, Grok, Hailuo, Topaz).
- Installed 8 Higgsfield companion skills via `npx skills add higgsfield-ai/skills -a claude-code`: brandkit, generate, marketplace-cards, product-photoshoot, soul-id, video-explainer, websites, youtube-thumbnail.
- Installed scroll-world the same way (`npx skills add oso95/scroll-world -a claude-code`). All 9 skills live in `~/.claude/skills/`.
- Created `~/Projects/scroll-world/.venv` with Pillow 12.3.0 for the optional `knockout.py` transparency step (Homebrew python3 is PEP 668 externally-managed, so a venv beats `--break-system-packages`).
- Verified ffmpeg/ffprobe present; Codex CLI present, so scene stills can bill to the ChatGPT sub instead of Higgsfield credits.

**What's live / deployed:**
- Nothing deployed. Local tooling only.

**Next up:**
- First real scroll-world build. Nothing has been rendered yet, no test generation was run.
- Optional: Monid CLI (monid.ai) is scroll-world's default video backend, pay-per-clip, roughly $27 for a 6-scene 1080p chain. Not installed. Without it the skill falls back to Higgsfield credits, and 345.11 credits will not carry a full 6-scene chain plus a mobile 9:16 chain.
- Open question Yeti has not answered: whether to build a connector-based fork of scroll-world so Cowork/Mobile can drive it.

**Notes for other environments:**
- The Higgsfield MCP connector (claude.ai) and the Higgsfield CLI are two different things. Cowork and Mobile already have the connector, so they can generate images and video there today. The CLI install was IDE-only.
- The skills CLI agent flag is `claude-code`, not `claude`. `-a claude` is rejected as an invalid agent.
- scroll-world as written shells out to `higgsfield`, `monid`, and `ffmpeg`. The claude.ai sandbox has none of those, so uploading the skill to claude.ai gets the interview, prompts, and scrub engine but stalls at render. Rendering stays on the Mac.
- Several Bash calls were blocked by the auto-mode permission classifier (`cp` into `~/.claude/skills`, `zip`, `npm view`, `higgsfield auth token`). `npx skills add` is the sanctioned installer and works.