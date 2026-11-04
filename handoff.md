
## Session: 2026-11-04 ET (signing outage)
**Environment:** Antigravity IDE
**What was done:**
- Found signing has never worked on OnPoint Office live: 0 signature files, 0 signature rows, 0 contracts signed in the app
- Commit 8898a9f saves signatures through the server for contracts, change orders, final walk and snow agreements

**What's live / deployed:**
- d1285a0 live. 8898a9f needs Yeti's push: git push origin feature/remote-signing:main from ~/Projects/onpoint-office-esign

**Next up:**
- Push, sign test job 1018, run scripts/diag-signing.mjs, expect SIGNED IN THE APP: 1
- Certificate upload and job photo test: only the documents bucket has files on live, so browser uploads may fail more widely

**Notes for other environments:**
- Devon stays on paper until the test signing passes