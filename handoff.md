
## Session: Oct 9 2026 ET (build)
**Environment:** Antigravity IDE
**What was done:**
- Yeti chose to BUILD the OnPoint CRM. Milestone 1, the snow visit log, is built in ~/Projects/onpoint-office (local commit 5749417, no remote)
- Vite React PWA + local Supabase: schema with row-level security, an offline outbox, phone + PIN login, EN/ES
- Crew and office screens built by Sonnet agents, reviewed and integrated by Opus
- 30 tests pass; e2e passes on iPhone (WebKit) and Android (Chromium) engines, including offline capture and sync on reconnect
- Fixed Safari IndexedDB Blob refusal and the WebP thumbnail issue (memory safari-pwa-offline-gotchas.md)

**What's live / deployed:**
- Nothing. Local only (Docker Supabase on the Mac)

**Next up:**
- Yeti: create a Supabase project, run `npx supabase login` in ~/Projects/onpoint-office, OK a Vercel project at app.onpointjd.com
- Real crew list (name, phone, role, truck, language) + prime contractor + direct accounts
- Ask Jay: does the prime round billing to 15 minutes?
- Push the repo to a PRIVATE GitHub repo when Yeti says

**Notes for other environments:**
- Local Docker Supabase is running on the Mac; `npx supabase stop` in ~/Projects/onpoint-office frees about 2 GB of RAM