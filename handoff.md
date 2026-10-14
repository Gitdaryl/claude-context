
## Session: 2026-10-13 ET (PIN self-service)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: Change my PIN (commit d8bf0cd). "My PIN" button in the top bar for everyone; sheet asks current PIN + new PIN twice. Server action change_pin on /api/members verifies the current PIN by signing in with it, enforces role length (6 crew / 8 office) and the weak-PIN rule, audits every try (pin_change), caps at 5/hour, ends all sessions; sign-in screen then says to use the new one. Migration 20261030000000_pin_change.sql pushed to production. Yeti added Devon, Linda, Jay and Kyle on the Team tab; PINs still to hand over in person.

**What's live / deployed:**
- onpoint-office main d8bf0cd, Vercel production Ready, bundle verified on app.onpointjd.com. Prod DB migration applied.

**Next up:**
- Hand each person their first PIN in person; they change it themselves from My PIN after first sign-in.
- Existing jobs: tap Change on the salesperson line and pick Devon (now that he exists).

**Notes for other environments:**
- Local seed crew PIN 555555 is "weak" by the app's rule, so the app refuses to set it; restore via admin API, not the app.