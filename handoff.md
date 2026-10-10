
## Session: Oct 10 2026, night ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- Yeti decided Google Business posts are his curated job (drone shots, QA), not a crew/office workflow: removed the "For Google" switch, Google pack and auto-post seam from OnPoint Office (commit 9010f99). The customer's yes/no to photos online stays, shown on the job's Photos.
- Subs upload photos that the customer link, insurance report and OnPoint records see (already built; test added).
- A rare WebKit hiccup after "Choose this" in present mode (once in ~25 runs) could not be reproduced; the flow now saves a screenshot and the page text if it recurs.

**Next up:**
- GBP API application around Dec 1 is now for reviews (sync + replies), not posting.