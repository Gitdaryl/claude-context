## Session: 2026-11-20 ET (later, same session)
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal (https://samquisenberry.vercel.app, code ~/Projects/sam-portal): added "Ask for a new look". Sam describes a look or taps one of six starter ideas, sees its status and any note from Yeti, and can take it back before work starts.
- New tool tools/add-look.mjs pulls a finished HeyGen look into the portal. It refuses looks that are not Sam's, are not portrait, or are on its block list (two Red Wings looks, the driving look).
- Watcher now shows a Mac notification for each new look request.
- Long topics now wrap in the Topic field.
- Pixabay API key saved at ~/.config/pixabay-api-key and tested for b-roll (Pexels has paused new keys).

**What's live / deployed:**
- samquisenberry.vercel.app with the look-request feature. Tested against the live store; probe data deleted.

**Next up:**
- Daryl: decide whether a new look is free to Sam or a line item, before sending him the link.
- To fulfil a request: make the look in the HeyGen web app (the CLI only makes template looks), then `node tools/add-look.mjs <lookId> "Name"`, `vercel deploy --prod --yes`, and set the request to Ready on the admin page.
- Stage 2 unchanged: subtitles, Pixabay b-roll, end card, finished-video preview, Meta posting.

**Notes for other environments:**
- Approval and look-request emails are not configured; the only alert is a Mac notification from the watcher.