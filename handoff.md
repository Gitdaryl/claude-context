# Session Handoff

## Session: July 17, 2026 (ET)
**Environment:** Antigravity IDE
**What was done:**
- Diagnosed the Never Broken bookmark QR failure: dynamic QR from qr-code-generator.com, account lapsed, qrco.de redirect disabled
- Found the source account via macOS "Where from" metadata on ~/Downloads/Photos/"joeprofitneverbroken.com QR code.png": app.qr-code-generator.com, download ID 90246622, QR contents https://qrco.de/bgh3HY -> www.joeprofitneverbroken.com
- Yeti found the account, upgraded to a YEARLY plan (10,000 scans included); verified via curl that qrco.de/bgh3HY now 302-redirects correctly. Printed bookmarks work again
- Created Google Calendar reminder July 6, 2027 (renewal ~July 17, 2027) so the subscription never silently lapses

**What's live / deployed:**
- qrco.de/bgh3HY redirect re-enabled; all printed Never Broken bookmarks functional

**Next up:**
- Future print runs: use a static QR or a self-hosted redirect (e.g. yetigroove.com/qr/joe) so print assets never depend on a third-party subscription
- Keep an eye on the 10,000-scan allowance if distribution scales up

**Notes for other environments:**
- The trick that found the account: `mdls -name kMDItemWhereFroms <downloaded file>` shows the download URL. Works for any browser-downloaded file
- QR account lives under admin@yetigroove.com (calendar event created there)