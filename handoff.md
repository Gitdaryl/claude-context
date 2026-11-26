## Session: Nov 25 2026 ET
**Environment:** Antigravity IDE
**What was done:**
- Planned the single "person" record for Holly's desk. Plan file: ~/Clients/holly-griewahn/PERSON-RECORD-PLAN.md (10 decisions, data model, import spec, 8 build chunks with a checkable output each). No code changed.
- Decisions: lives in Holly's own desk (not Office); one person with many buy/sell episodes; new private Blob store with append-only change files; leads, texts, roadmaps and newsletter status attach at read time by phone then email; permission hangs on the phone number or email address; one importer for the Mailchimp zip and the past-sales CSV, run as a desk screen (dry run, then commit of exactly that plan).
- Holly's pending answers became settings with safe defaults. Only the real import run waits on her.
- Board: design row closed with the plan as evidence, Mailchimp import row updated (one importer feeds the Letter tab and the cards), five rows filed.

**What's live / deployed:**
- Nothing. Planning only.

**Next up:**
- Yeti (Today): create the private Blob store holly-people, isolate the Preview environment (test stores, no Twilio), optional sample Mailchimp export for real headers.
- Yeti (Today): say whether hollygriewahnrealtor.com is the final site address. The newsletter send gate still looks for hollygriewahn.com, so sending cannot switch on as things stand.
- Yeti (Today): land or drop the roadmap texting patch (~/Clients/holly-griewahn/deal-text-consent.patch) before the People tab is built.
- Sonnet: build chunks 0 to 5 from a clean worktree off origin/main.
- Backlog: the local Holly-main checkout is 7 commits behind with 36 uncommitted files; rescue or drop in its own session.

**Notes for other environments:**
- Line references in the plan are against origin/main at 04b0ffe, not the local checkout.
- The Holly site repo is public: her contact files never go in the repo folder; fixtures are synthetic only.
- The brief's "do first" fixes (search, filters, lead cap, lead to roadmap link) shipped Nov 25 in 04b0ffe.