
## Session: Oct 14 2026 (late), Meta token fix
- Meta rejected the first CAPI token ("Invalid application ID"): the pbpaste pipe had captured command text instead of the token. Yeti re-entered it via the interactive `vercel env add` prompt on both projects; redeployed both with `vercel redeploy`.
- /api/track now awaits the Meta send in full and logs the answer (commit 91bebeb); a 1.5s race could leave the function frozen before the send finished.
- VERIFIED: server log `track meta tap-m2wait1-abc111 {"ok":true,"received":1}`. Meta receives events with test code TEST44463.
- Memory added: secret-entry-interactive-prompt.