## Session: 2026-11-20 ET (follow-up to the DigitalOcean alerts review)
**Environment:** Antigravity IDE
**What was done:**
- Rebooted yeti-vps with Yeti's OK to load the pending kernel and libc6 updates.
- Verified from inside and outside after boot.

**What's live / deployed:**
- yeti-vps booted Nov 20 18:10 UTC on kernel 6.8.0-149 (was 6.8.0-124, up since Jun 14). reboot-required cleared, 0 failed units.
- nginx, n8n, cloudflared, yeti-mcp, pm2-root, cron and ssh all active. Node 22.23.5. n8n on 127.0.0.1:5678, port 5678 closed from outside, https://n8n.yetigroove.com/healthz returns 200, all 6 workflows re-activated.

**Next up:**
- Add NodeSource to unattended-upgrades so Node patches itself. Backlog row on the Master Task Board.
- Turn on ufw (allow 22, 80, 443), needs Yeti's OK. Backlog row on the Master Task Board.

**Notes for other environments:**
- Anything that used to call n8n at http://143.198.171.9:5678 directly must now use https://n8n.yetigroove.com.
- Node on the VPS comes from NodeSource and does not auto-update. Ubuntu packages (nginx etc.) do.