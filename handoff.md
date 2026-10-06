
## Session: 2026-10-06 ET
**Environment:** Antigravity IDE
**What was done:**
- HeyGen is retiring all v1/v2 endpoints on Nov 1 2026. Inventoried every HeyGen call across ~/Projects, ~/Documents/Claude Code, ~/.claude tools and skills.
- Manitou-Beach scripts/holly-render.js: status poll moved from v1/video_status.get to GET /v3/videos/{id}; keeps polling through 429/5xx; surfaces v3 failure_code/failure_message. Create call was already v3.
- YetiClone api/_heygen.js, api/video-status.js, api/avatars.js: moved to v3 (GET /v3/videos/{id}, GET /v3/avatars + /v3/avatars/looks with cursor pagination). The v2 "match video avatar by list index" hack is gone; look id is the avatar_id.
- media-use skill, holly-reel-kit, hyperframes: already v3, nothing to change.
- Verified by mocked-fetch tests + builds. Could NOT live-test: the YetiClone HEYGEN_API_KEY (same value in Vercel prod and .env.production) returns 401 on every endpoint, so it has been revoked on HeyGen's side. Holly's key (GitHub secret) works: Oct 1 render succeeded.

**What's live / deployed:**
- Manitou-Beach origin/main 19bc131 (pushed from a clean clone; local main still carries the same change as 5e231a1 plus unrelated uncommitted work from another machine, left untouched)
- YetiClone origin/main 9e54c3a -> Vercel auto-deploy

**Next up:**
- Yeti: issue a new HeyGen API key, update the yeticlone Vercel env (rotate-env.py) and local .env.production. Then open /admin clients in YetiClone and confirm the client avatar group id e4bc6858... still matches what v3 returns (v3 docs show ag_ style ids; unverified whether legacy hex ids carried over).
- After the new key: `curl -s https://api.heygen.com/v3/avatars/looks?ownership=private -H "x-api-key: $KEY"` and check each look's supported_api_engines includes avatar_v, since generate.js hardcodes that engine.
- First Wednesday Holly run after this (Oct 7, 8pm ET) proves the v3 poller live; check the Actions log for "status: completed".

**Notes for other environments:**
- Any v1/v2 HeyGen call anywhere dies Nov 1 2026. Legacy responses carry Deprecation: true + Sunset header + a warning.v3_endpoint field.