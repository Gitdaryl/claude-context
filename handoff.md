## Session: 2026-08-15 to 16 ET
**Environment:** Antigravity IDE

**What was done:**
- Assessed CoAuthor.ai (AI book SaaS, $48 to $749/mo) for duplicability. The product duplicates easily, the business does not. Their moat is publishing credibility and distribution, not software.
- Built `~/Projects/kdp-studio`, a self-owned replacement running on tools already paid for. Live private repo at Gitdaryl/kdp-studio.
- Two modes over one drafting engine. **market**: research-first KDP non-fiction. **ghost**: client memoir or business story built only from interview transcripts and documents. Ghost mode is the Never Broken pattern made repeatable.
- Core rule enforced in code: the model drafts prose, the source supplies facts. Unsourced facts get `[VERIFY: question]` inline and `build.sh` exits 2 rather than build a final manuscript.
- Eleven stages: research or interview, bible, outline, draft, edit, images, metadata, cover, build, preflight, publish or deliver. Each has a definition of done checked against the files.
- Dashboard (`scripts/serve.py`) derives every stage from what is on disk, so progress cannot drift. New-book wizard asks who the book is for first, since that decides where facts come from. Refreshes every 4s.
- Demand explorer (`scripts/trends.py`, also `/trends`): Google autocomplete for what the web asks, Amazon book autocomplete for whether it has become book buying yet. No API key needed. A question with demand and nothing claiming it is the opening. Explicitly not search volume, and it says so on the page.
- Templates: bible with mandatory pasted voice sample, outline, interview guide with question banks and consent checklist, source log, style sheet, KDP metadata, image plan, and a 40-box preflight including the KDP account and tax interview.
- `--tailscale` flag binds the dashboard to the tailnet address for phone access. Fails closed rather than falling back to 0.0.0.0.
- Wrote `docs/client-portal-spec.md`, the brief for a client chapter-review portal. Deliberately not built.
- Skill at `~/.claude/skills/kdp-studio/SKILL.md` drives the whole thing.

**What's live / deployed:**
- Private GitHub repo Gitdaryl/kdp-studio, pushed through 797ebed. Tooling and templates only, `source/` and `build/` gitignored so client material never leaves the Mac.
- pandoc installed via brew. Nothing hosted anywhere, on purpose.

**Next up:**
- Yeti to install Tailscale for phone access: `brew install --cask tailscale`, sign in, then `python3 scripts/serve.py --tailscale`.
- No KDP account yet. The preflight checklist covers account, tax interview and bank details.
- DataForSEO is NOT configured on this Mac despite the skill and agent existing. Market research falls back to WebSearch plus trends.py.
- Build the client review portal only when a real ghostwriting client is mid-book. Spec is in the repo.

**Notes for other environments:**
- Trigger phrase for later: "I have a ghostwriting client, build the review portal" points at `docs/client-portal-spec.md`.
- Cowork: cover generation and reading market research fit there. Drafting and builds belong in the IDE.
- Yeti watched a video pitching KDP as a low-friction business. Flagged that the easy non-fiction categories are saturated and only first-hand knowledge still earns.