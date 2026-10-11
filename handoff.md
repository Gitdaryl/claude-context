## Session: 2026-10-11 (ET), afternoon
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD: emergency tarping night loop (morning), then the full diorama set: nine service cards on the home page, six service-page heroes (roofing, gutters, siding, windows, power washing, commercial), the snow hero, and the home commercial block all run matching loops of ONE house, one job each. Nano Banana Pro edits off one daytime base, Kling 3.0 pro locked camera, crossfade loops, lazy-loaded cards, posters under reduced motion, phones keep the icon list.
- Judged by measurement (camera-lock border std, moving %, seam wrap step, heat maps, frame strips). Rejected and re-rendered: 5 takes for Kling spawning 3D cloud puffs from "clouds drift", 2 siding takes for slow zoom.
- Scripts: ~/.claude/tools/stormloop.py, ~/.claude/tools/cardloop.py. Memory: storm-loop-lightning-seam (corrected: Nano Banana reference edits work; pick the /hf_ output URL), kling-containment-prompt-rule (cloud rule).

**What's live / deployed:**
- onpointjd.com commits f4a1314 (storm loop), 76e391a (nine cards) and 41b5832 (heroes, snow hero, home commercial), all pushed from a clean worktree on origin/master and verified headlessly at desktop, tablet and phone widths.

**Next up:**
- Yeti reviews the loops on the live site (home cards, /roofing hero, /snow hero, home commercial). Anything he dislikes is a 2-credit still edit + 7.5-credit Kling take to swap.
- Local on-point-jd master divergence is OWNED by another IDE session (board row "decide when to ship the local-only commits", In Progress). Origin moved 3 commits today; that session must rebase onto the new tip.

**Notes for other environments:**
- Do not pass concurrent Higgsfield CLI generate calls; upload first, then generate by id with a retry loop.
- Never write "clouds drift" in a Kling prompt on a plain-background diorama.