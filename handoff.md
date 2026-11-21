## Session: 2026-11-21 (evening) ET
**Environment:** Antigravity IDE
**What was done:**
- Sam Quisenberry portal (~/Projects/sam-portal): built posters. A poster is a fixed HTML template with real type (three styles: Photo, Checklist, Big words), so making one costs nothing.
- Found Yeti's real Feb 2026 portraits of Sam and his team on the NAS (personal_folder/Yeti Groove/Clients/Sam -State Farm/FEB photoshoot/Lightroom export) and used four suit portraits plus one team shot.
- Wrote 11 ready poster ideas from the reel scripts (data/poster-ideas.json). Nobody has read the wording yet.
- Portal: Reels / Posters tabs, a menu of live-drawn posters, a builder with live preview, "Order for $20", "Take it back". Watcher draws the 2160x2700 PNG and texts Yeti.
- Tests: 85 local page and API checks, 9 watcher checks, 24 live checks on production.
- Earlier the same day: email to Sam turned on; end card filled from his public State Farm page; advice given to keep the end card navy.

**What's live / deployed:**
- https://samquisenberry.vercel.app redeployed with posters built in but switched OFF for Sam (showToSam false in data/poster.json). Yeti's admin link shows the Posters tab.
- Nothing sent to Sam, nothing posted, no credits spent. Not committed to git.

**Next up:**
- Yeti: look at ~/Previews/2026-11-21 Sam posters (three styles, all 11 ideas, the builder).
- Yeti: set the poster price ($20 is Claude's suggestion) and read the poster wording.
- Yeti: when ready for Sam, set showToSam true in data/poster.json, then `cd ~/Projects/sam-portal && vercel deploy --prod --yes`.
- Ask Sam whether his three staff are OK appearing in ads (team photo).
- Not built: scene pictures in the Sunny Skies style, carousels, schedule menu, b-roll, Meta posting.
- Still owed from earlier: watch the finished video sample, Sam's yes on end card details and footer line, help clip by ear, five winter looks, read the 11 scripts, send Sam his link, tell him looks are $24.

**Notes for other environments:**
- Board row "Sam Quisenberry posters: look at the samples, set the price, say when Sam gets the tab" is in Today.
- Real photos of Sam live on the NAS path above; use them before any AI look.