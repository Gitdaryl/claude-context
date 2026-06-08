## Session: 2026-06-08 AEST
**Environment:** Antigravity IDE

**What was done:**
- Added global pause switch to Sunny Skies VPS dispatcher (tracking.json paused flag, pause.sh + resume.sh scripts)
- Built standalone Dispatcher Admin UI — dispatcher-admin-six.vercel.app (React+Vite+Tailwind+dnd-kit)
- All 3 time slots (9am, 12pm, 6pm) fully drag-and-drop configurable — Quotes is no longer hardcoded to 9am
- Per content type on/off toggles
- VPS config server running on port 3847 via PM2, boot-persistent (pm2 startup + pm2 save done)
- Vercel API proxies to VPS config server — no Vercel KV/storage needed
- VPS dispatcher updated to read remote config, respect disabled types, use schedule-driven slot assignment, fall back to hardcoded defaults if config server unreachable
- PM2 installed on VPS, ss-config process saved for reboot persistence

**What's live / deployed:**
- dispatcher-admin-six.vercel.app — Sunny Skies control panel
- VPS config server: 143.198.171.9:3847 (PM2 managed)
- dispatcher.js on VPS fully updated

**Next up:**
- Adding new content type (e.g. Testimonials): needs Google Drive source folder + Posted subfolder, repurpose.io workflow, add to CONTENT_TYPES array in dispatcher.js, add to TYPE_META in admin UI src/lib/typeMeta.js and defaults.js

**Notes for other environments:**
- Dispatcher admin URL: dispatcher-admin-six.vercel.app
- To pause dispatcher remotely: tell Claude "pause Sunny Skies" (runs /root/SunnySkies/pause.sh via VPS MCP)