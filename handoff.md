## Session: 2026-11-23 10:22 PM ET
**Environment:** Antigravity IDE
**What was done:**
- Turned on the Claude Code advisor by default: added `"advisorModel": "fable"` to `~/.claude/settings.json` (user settings). The `fable` alias tracks the newest Fable each install knows about.
- Verified per install with `claude -p "/advisor"`: Antigravity IDE extension 2.1.325 and 2.1.330 report "Advisor: Fable 5.2". Claude Desktop Code tab (2.1.330) reports Fable 5.2. VS Code extension 2.1.296 and Homebrew CLI 2.1.281 report Fable 5.1 (older build). nvm CLI 2.1.177, which is first on PATH and is what the terminal and all launchd jobs run, says "/advisor isn't available": too old.
- Confirmed the advisor tool actually fired in the IDE session.

**What's live / deployed:**
- Advisor on for every new Claude Code session in the IDE and the Desktop Code tab on this Mac. Nothing pushed or deployed.

**Next up:**
- Yeti: upgrade the terminal CLIs so the terminal gets the advisor too (commands on the Master Task Board row). Decide first whether the scheduled jobs (lead-catcher, ops-watch, sitdown-watch, social-insights) should get the advisor; if not, add `export CLAUDE_CODE_DISABLE_ADVISOR_TOOL=1` to their run.sh before upgrading, because Fable as advisor bills to usage credits.

**Notes for other environments:**
- The setting lives in a file on the Mac. Cloud sessions (claude.ai/code in a browser, the Code tab on mobile) do not read it: type `/advisor fable` in each cloud session. Ordinary Claude chat and Cowork chat have no advisor feature.
- Turn it off: delete the `"advisorModel"` line from `~/.claude/settings.json`, or run `/advisor off` in a terminal session. Check it: `/advisor` with nothing after it.