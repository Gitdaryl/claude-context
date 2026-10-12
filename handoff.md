
## Session: 2026-10-12 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: new "YetiGroove support" role (owner-level, hidden from team lists, owner-only on/off switch, changes audit-logged)
- Crew (roof/snow) now only required for field roles; office/sales/owner can be "No crew"; bookkeeper/support never
- Team texts: new Office group (owner, office, sales, bookkeeper)
- 938 + 21 new tests pass on a fresh DB; Playwright screen check tests-e2e/support-office.mjs passes

**What's live / deployed:**
- onpoint-office bef83a5 pushed to main (Vercel auto-deploy), INCLUDING the earlier unpushed RoofIT wave commits
- Live Supabase NOT migrated yet: 20261026000000, 20261027000000, 20261027100000 pending (auto mode blocked db push)

**Next up:**
- Yeti: `cd ~/Projects/onpoint-office && npx supabase db push` NOW (live sign-in likely broken until then)
- Yeti: convert own live login to support: `npm run add-member:live -- --phone <your 10 digits> --name "Daryl" --role support` (asks for a PIN, 8+ digits; this sets the PIN)
- Show Jay the Team tab support card before Devon's demo

**Notes for other environments:**
- Pitch to Jay: support access is his switch; every change logged under Daryl's name