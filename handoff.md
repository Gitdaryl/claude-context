## Session: 2026-07-13 ET
**Environment:** Antigravity IDE
**What was done:**
- Scanned local repos for Remotion usage; found two: Manitou-Beach and Yeti-Signature-Films/stays-broll
- Upgraded both to Remotion 4.0.489 (latest) via `npx remotion upgrade`
  - Manitou-Beach: was 4.0.441 (remotion, @remotion/cli, @remotion/player; zod also bumped to 4.3.6)
  - stays-broll: was 4.0.261 (remotion, @remotion/cli)
- Verified: Manitou-Beach vite build passes; both Remotion bundles compile and list all compositions (EventPromo, StaysPromo, GetListedPromo; StaysBroll)

**What's live / deployed:**
- Nothing deployed — local package upgrades only, not committed or pushed

**Next up:**
- Commit/push the package.json + lockfile changes in both repos if the upgrades should stick
- Optional: Manitou-Beach vite build warns about >500 kB chunks (pre-existing, not from this upgrade)

**Notes for other environments:**
- Remotion is now pinned exact at 4.0.489 in both repos (remotion upgrade uses --save-exact)