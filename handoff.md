
## Session: 2026-09-20 ET
**Environment:** Antigravity IDE
**What was done:**
- Updated HyperFrames Claude skills via `npx hyperframes@latest skills update` (8 outdated refreshed, new core skill `hyperframes-studio` installed; `skills check` now reports 10 current, 0 outdated).
- Found HyperFrames CLI 0.8.55 now requires Node >= 22. Mac's nvm default is still Node 20; ran the update under `nvm use 22` (v22.23.2 already installed).
- Verified Holly weekend automation is unaffected: both GitHub Actions jobs (ubuntu + self-hosted Mac Studio) pin Node 22 via setup-node, and run.mjs calls `hyperframes@latest`.

**What's live / deployed:**
- Nothing deployed. Skills live in ~/.claude/skills and ~/.agents/skills.

**Next up:**
- Decide whether to make Node 22 the nvm default on the Mac (`nvm alias default 22`) so interactive `npx hyperframes` works without `nvm use 22`. holly-reel-kit/reel/package.json scripts still pin 0.8.4; run.mjs (the unattended path) uses @latest.

**Notes for other environments:**
- Any `npx hyperframes` on the Mac from a Node 20 shell now fails with "requires Node.js >= 22". Prefix with `source ~/.nvm/nvm.sh && nvm use 22`.