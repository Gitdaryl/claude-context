## Session: 2026-10-10 ET (v2 goes live)
**Environment:** Antigravity IDE
**What was done:**
- Yeti approved the Holly v2 renders and chose to replace the classic edit starting Wed Oct 14.
- Hardened v2 for unattended weeks: approved-script text on screen (whisper timings), no-hook path, balanced hook wraps, stamp text fix, caption chunking, music bed extends for long takes (up to 135s tested), chips re-copied weekly, carve vendored.
- Tested v2 on Sep 3, Sep 24, Oct 1 and Oct 8 takes (73-135s): all pass hyperframes check.
- Wired v2 into holly-reel-kit/reel/run.mjs as step 11 with the classic edit as automatic fallback. Rehearsed the full production path in a scratch copy: v2 delivered; forced v2 crash delivered classic and produced the fallback note.
- Verified Lyria music terms: Gemini API ToS, Google claims no ownership, no commercial restriction stated.

**What's live / deployed:**
- reel/run.mjs change is on disk on the Mac Studio, which is what the self-hosted runner executes Wednesday. Uncommitted (repo has no remote).
- v2/ folder is untracked in holly-reel-kit.

**Next up:**
- Wed Oct 14 8pm ET: first unattended v2 reel. Board row in Waiting. Kill switch: mv ~/Projects/holly-reel-kit/v2/make.sh ~/Projects/holly-reel-kit/v2/make.sh.off
- HeyGen CLI install + oauth login for licensed music (Today row).
- Business Spotlight v2 and business media gap (Backlog).

**Notes for other environments:**
- If Yeti asks Cowork/Mobile why the Holly reel looks different from Oct 15 on: it is the v2 edit (hook, camera cuts, music, SFX).