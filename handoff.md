
## Session: Oct 9 2026 ET (invoices)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: structured addresses, formatted phones, directions links (Apple Maps on iPhone, Google elsewhere), tap-to-call
- Pricing dropdown (hourly per truck, per push/salting, per storm, seasonal, monthly, quoted), billing frequency, terms, payment method
- Invoices tab: Ready to bill, drafts, finalize INV-0001, printable branded invoice with proof of visits, payments (check/cash/Venmo/Zelle/card/ACH), void
- Commits 13da752, 81acaf1, 1a7cc17 in ~/Projects/onpoint-office (local, no remote). 57 tests + snow and invoice browser flows pass on iPhone/Android engines

**What's live / deployed:**
- Nothing. Local Docker Supabase + vite preview on the Mac

**Next up:**
- Customer proof link + email invoices (Resend), crew pay sheet, notifications (texts once Twilio A2P is approved)
- Deploy: Yeti creates a Supabase project + `npx supabase login`, OKs a Vercel project at app.onpointjd.com

**Notes for other environments:**
- Invoices never run payroll or the books: QuickBooks stays the ledger, a payroll service handles W-2 taxes