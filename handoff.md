
## Session: 2026-10-13 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office (app.onpointjd.com): Measure screen now has a Decking field (sheets of 7/16 OSB known bad). Roof pricing adds a "Decking replacement, N sheets" line at the price book sheet price ($50) to both options, outside the roof price and after any minimum. Assumption note updated. EN + ES. Tests added (997 pass). Commit 900c70d.

**What's live / deployed:**
- onpoint-office main 900c70d, Vercel production Ready, bundle verified on app.onpointjd.com.

**Next up:**
- Materials order does not yet add the counted OSB sheets; decking photos after tear-off still bill ALL counted sheets as a change order, so a crew count that includes the sheets already on the estimate would double bill. Decide whether the change order should subtract deckingSheetsEst.

**Notes for other environments:**
- webp-sweep again converted tests/fixtures/ruler.jpg in onpoint-office; reverted before commit (known trap).