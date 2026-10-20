
## Session: 2026-10-20 ET
**Environment:** Antigravity IDE
**What was done:**
- Found onpointjd.com/estimate was NOT wired to the Office Roof prices card (own /desk book at $715; Office saved $800 on Oct 17). Low pitch priced below Standard because the site shrank the roof and had no Low percent.
- Office: GET app.onpointjd.com/api/public/roof-rates; price-book basics moved to src/lib/jobs/roofBook.ts (9387eb8).
- Website: /api/offer prices from the Office card; calculator uses the Office's per-answer percents; Low sized like Standard + its 3%; /desk shows Office prices read only, edits only the range spread; page build bakes in the live Office prices (88de8f2).

**What's live / deployed:**
- Both deployed and verified in a headless browser: typical 1,800 sq ft house Standard $20,200-$25,800, Low $20,800-$26,600 (+3%), 28 squares each.

**Next up:**
- Devon decides: Office charges 2 layers +3% but the site promises the 2nd layer free (CONFIRM.md).
- After any Office price change, rebuild on-point-jd (build_pages + stamp_assets) and push so FAQ/llms prices match.
- Another session has uncommitted work in ~/Projects/on-point-jd (build_pages.py + generated html): it must pull, rebase, and rebuild before pushing.

**Notes for other environments:**
- Prices now change in ONE place: OnPoint Office, Costs tab, Roof prices.