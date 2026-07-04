## Session: 2026-07-04 ET
**Environment:** Antigravity IDE

**What was done:**
- Traced the "missing" Lake Access Media order (Dennis Babjack, for The Rivers Edge Event Center / Ryan Kinsey). Found there is NO orders database: the form at yetigroove.com/social (repo Gitdaryl/Yeti-Groove, on Vercel, not the VPS) POSTs to /api/social-submit, which only emails daryl@yetigroove.com (Resend) + texts 517-260-5907 (Twilio). The order lives only in that inbox + phone. Photos come as a Drive LINK pasted into "Media Notes".
- Confirmed both of Dennis's bug reports: (1) shared Drive folder is share-set to Viewer (anyone:reader) so uploads are blocked; (2) the "3 ways to tell your story" cards were decorative and didn't map to the 9 selectable example styles.
- Fixed both bugs in social.html + lakeaccess.html: 3 cards are now clickable filters mapped to the 9 styles (photos/mix/promo), paste-a-link is now the primary media path, and the order SMS now names business + style + price.
- Opened PR #1: https://github.com/Gitdaryl/Yeti-Groove/pull/1

**What's live / deployed:**
- Nothing merged yet. PR #1 is open on branch fix/social-order-form; Vercel should build a preview.

**Next up (needs Yeti, outside code):**
- Merge PR #1 after eyeballing the Vercel preview.
- Set the Drive folder (1wApVLL50JpWHpRT7N-4jX7YEzydFk4Zc) link access to Editor if you want the direct-upload button to work.
- Confirm TWILIO_ACCOUNT_SID / TWILIO_AUTH_TOKEN / TWILIO_PHONE env vars exist in the Vercel project, or SMS stays silently off.
- Reconnect the Gmail connector (it's expired) to pull Dennis's actual order email + Ryan Kinsey's follow-up.
- Review the style->bucket mapping in the PR; swap any styles between the 3 buckets if the taxonomy is off (one-line data-group edits).

**Notes for other environments:**
- Lake Access Media = video production by Yeti Groove Media; two intake pages: /social and /lakeaccess (partner-priced). Same backend, same 9 styles.