## Session: July 20, 2026 (ET), part 6
**Environment:** Antigravity IDE
**What was done:**
- Designed the Redo Loop for lookbook collaboration and added it to ~/living-draft/SPEC.md: explicit "request a redo" verb per print (notes stay conversation), image-EDIT against current version via Fal (never re-roll: keeps face/pose/room so old-vs-new is a real comparison), version stack taped over old prints with instruction-as-label ("v2 - 'wears pink' - Joe, Jul 20"), PROPOSED stamp + KEEP/TOSS approval, n8n only for pings, render loop site-native (/api/redo + Fal callback)

**What's live / deployed:**
- No site changes this part; both sites unchanged from part 5 (hardened notes stack live on never-broken + long-shutdown)

**Next up (blocked on Yeti, both are env-var handoffs):**
1. FAL_KEY for the long-shutdown Vercel project -> I build and test the Redo Loop end-to-end (~/api/redo, Fal queue callback, version-stack UI)
2. n8n webhook URL -> activates note email/SMS pings on both sites (NOTIFY_WEBHOOK_URL env var, payloads already carry site field for routing)

**Notes for other environments:**
- SPEC.md is the product source of truth; Redo Loop is the flagship differentiator ("argue with the image and it changes")