
## Session: 2026-11-08 ET
**Environment:** Antigravity IDE
**What was done:**
- OnPoint JD comp Highlighted listing on manitoubeachmichigan.com/business/on-point-jd (Notion row, photos in MB Blob, hours, FAQ schema, UTM-tagged website link)
- MB fix 2abeae3: out-of-state listings no longer published as Michigan (title, location line, schema); website link shows without query string
- OnPoint 08cfb71 (pushed from a fresh clone; ~/Projects/on-point-jd is 4 commits behind with 65 stale dirty files, untouched): MB profile in sameAs, one contextual link on /service-area

**What's live / deployed:**
- Both commits live and verified headless

**Next up:**
- Paste OnPoint's Google Place ID into the MB row before Dec 1 (else the report-card cron texts OnPoint's lead line)
- When Jay's MI license issues: flip "We do not work in Michigan" (home FAQ, service area, llms.txt), add Lenawee service areas to the listing

**Notes for other environments:**
- ~/Projects/on-point-jd local checkout is behind origin with uncommitted Oct work; do not push from it blindly