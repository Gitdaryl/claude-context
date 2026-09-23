## Session: 2026-09-23 ET (v3 pushed)
**Environment:** Antigravity IDE

**What was done:**
- Pushed Never Broken treatment Draft v3. Commit `b063df2` on `main`.
- Ran the image sweep first per the build standard; it converted `images/joe-profit.png` to webp, 488 KB down to 23 KB, and rewrote the `index.html` reference. Verified the webp decodes at identical dimensions and left no dangling references.
- No build script on this repo (static site plus serverless `api/`), so verification was done against the deployed page instead.

**What's live / deployed:**
- **Draft v3 is live** at https://never-broken-site.vercel.app/treatment
- Deploy verified against the live URL rather than assumed: Draft v3 serving, 9 place-and-year cards, all 60 note anchors present, notes API returning 200, the `images/joe-profit.webp` serving as `image/webp`, and "nineteen" gone from the page.

**Gotcha worth keeping:**
- `/treatment.html` 302s to the clean URL `/treatment`. A `curl` without `-L` returns a "Redirecting..." stub, which reads exactly like a stale or failed deploy. It had actually been live the whole time. Follow redirects and assert on page content, never on a 200.

**Next up:**
- Tell Joe it's up. He does not know yet. Point him at the gold-edged "revised v3" paragraphs and the "Seven holes only you can fill" block at the bottom, where each item has its own note anchor so he answers in place. Do not summarise the draft for him.
- The climax question is now his, asked directly at nb-49.
- Re-record the LISTEN narration, but only after his v3 notes come back, since more text may still move. The clips are Joe's voice against the v2 text and now diverge on every revised paragraph. The page says so up front, so it is honest rather than broken.
- Still owed and unchanged: the production budget Joe's son needs before he can raise, and session 4 to finally get the barbecue.

**Notes for other environments:**
- `treatment.html` note anchors are load-bearing. Never renumber; only append. v3 went nb-39 to nb-60 and preserved all 38 originals.
- Before restructuring a client deliverable on craft grounds, check what that client has already been taught in writing. The original plan to move the film's climax was right in the abstract and wrong against `structure.html`, which Joe already holds.