## Session: 2026-11-20 ET
**Environment:** Antigravity IDE
**What was done:**
- Reviewed three URGENT DigitalOcean security emails against yeti-vps (143.198.171.9, Ubuntu 24.04).
- NGINX HTTP/2 alert (Nov 20): no action needed. Ubuntu auto-patched to 1.24.0-2ubuntu7.20 at 06:00 UTC and HTTP/2 was never enabled.
- PHP alert (Oct 21): does not apply. PHP is not installed.
- Node.js Brotli alert (Oct 23, CVE-2026-111497): applied. n8n was on Node 22.22.2. Upgraded to 22.23.5 and restarted n8n.
- Found n8n reachable from the internet on port 5678 over plain HTTP (bound to 0.0.0.0, ufw off). Bound it to localhost with a systemd drop-in: /etc/systemd/system/n8n.service.d/listen-localhost.conf.
- Light check for signs of compromise: nothing odd (one login account, SSH keys unchanged since Jun 8, cron is only field-office-monitor).

**What's live / deployed:**
- yeti-vps: Node 22.23.5, n8n 2.25.7 on 127.0.0.1:5678 behind nginx. Port 5678 closed from outside, https://n8n.yetigroove.com/healthz returns 200, all 6 active workflows re-activated.

**Next up:**
- Reboot yeti-vps for pending kernel and libc6 updates (needs Yeti's OK, about 2 minutes of n8n downtime). On the Master Task Board.
- Add NodeSource to unattended-upgrades so Node patches itself. On the Master Task Board.
- Turn on ufw (allow 22, 80, 443). Noted in the reboot row.

**Notes for other environments:**
- Anything that used to call n8n at http://143.198.171.9:5678 directly must now use https://n8n.yetigroove.com. Nothing was connected that way at the time of the change.
- Node on the VPS comes from NodeSource and does not auto-update. Ubuntu packages (nginx etc.) do.