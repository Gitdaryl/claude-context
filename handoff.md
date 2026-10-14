## Session: 2026-10-13 ET (continued)
**Environment:** Antigravity IDE
**What was done:**
- OnPoint Office: salesperson on the job (commit 5db1332). Job page line "Devon is the salesperson" with a picker (active owner or sales people). The estimate PDF, contract, emails and texts all read jobs.sales_rep, so a change shows on the next document or message. New jobs made by the office or by support (Daryl signed in as the owner) default to the team's one active salesperson, so Daryl's name stays off Devon's paperwork.

**What's live / deployed:**
- onpoint-office main 5db1332, Vercel production Ready, bundle verified on app.onpointjd.com.

**Next up:**
- Existing jobs still carry Daryl as salesperson until tapped once on each job page (Change > Devon > Save). A bulk fix script was blocked by the permission classifier; Yeti can tap through them or ask again in an interactive session.
- Materials order does not add the counted OSB sheets; change order after tear-off still bills all counted sheets (possible double bill with the new estimate line).

**Notes for other environments:**
- webp-sweep converts tests/fixtures/ruler.jpg in onpoint-office every run; revert before committing.