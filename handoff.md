## Session: 2026-08-15 ET
**Environment:** Antigravity IDE

**What was done:**
- Assessed CoAuthor.ai (AI book-writing SaaS, $48 to $749/mo) for duplicability. Verdict: the product duplicates easily, the business does not. Their moat is publishing-industry credibility and distribution, not software.
- Built `~/Projects/kdp-studio`, a self-owned replacement running on tools already paid for: DataForSEO for Amazon research, Claude for drafting, Nano Banana Pro or Higgsfield for covers, ElevenLabs for audiobook, pandoc for DOCX and EPUB.
- Two modes over one drafting engine. **market**: research-first KDP non-fiction, 40k to 55k words. **ghost**: client memoir and business story built only from interview transcripts and documents, 60k to 90k. Ghost mode is the Never Broken pattern made repeatable.
- Scripts, all stdlib and tested: `newbook.py`, `stats.py`, `continuity.py` (extracts names, years, ages, figures per chapter and surfaces age and date conflicts), `spine.py` (KDP wraparound cover math), `build.sh` (pandoc to DOCX and EPUB).
- Core rule enforced in code, not in a doc: the model drafts prose, the source supplies facts. Unsourced facts get `[VERIFY: question]` inline and `build.sh` exits 2 rather than build a final manuscript while flags remain.
- Templates: book bible with a mandatory pasted voice sample, outline, interview guide with question banks and a consent checklist, source log, style sheet, KDP metadata sheet.
- Docs: ghostwriting rules, market research method, KDP specs and policy notes.
- Installed pandoc via brew.
- Wrote the `kdp-studio` skill to `~/.claude/skills/kdp-studio/SKILL.md`, command-driven with a fixed stage order.
- Smoke tested end to end with a throwaway book, fixed a regex bug where names split across line breaks, then deleted the test.

**What's live / deployed:**
- Nothing deployed. `~/Projects/kdp-studio` committed locally at 1dfe20e. Not pushed to GitHub yet, needs a repo created.

**Next up:**
- Push kdp-studio to GitHub (repo does not exist yet).
- First real run when a ghostwriting client lands. Stage order is: new, two interview sessions, bible, outline, remaining interviews, draft, continuity, revise, metadata, cover, build.
- Context: Yeti watched a video pitching KDP as a low-friction business. Flagged that the easy non-fiction categories are saturated and the titles that still earn carry first-hand knowledge a model cannot produce.

**Notes for other environments:**
- Ghost mode `source/` folders are gitignored. Client transcripts stay local unless there is a decision to put them in a repo.
- Cowork: cover generation and market research reading are good fits there. Drafting and builds belong in the IDE.