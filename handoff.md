## Session: 2026-07-18 (ET, lookbook shipped)
**Environment:** Antigravity IDE
**What was done:**
- Generated and deployed the full cinematic lookbook: 11 concept frames (21:9, 2k) placed through the treatment, one leading each session: tracks cold open, the room, Joe mentoring (real likeness via Nano Banana Pro from reference/joe photos: Alpha portrait + ULM teaching shot), greyhound, kitchen, walk-on, barn, draft day, knee, deed signing, final session
- Tools: Higgsfield Cinema Studio 2.5 for period frames, Nano Banana Pro for identity frames; Joe refs uploaded to Higgsfield (media ids in git history of this file if ever needed)
- Quality control mattered: THREE frames initially generated with white subjects (Marcus, the kitchen family, the entire draft-day family) and one with wrong-period set dressing; all caught on review and regenerated with explicit casting/period language. Rule: every generated frame gets eyeballed before Joe or any funder sees it
- Frames captioned "concept frame" for honesty in funder materials; no NFL/team marks anywhere; barn frame is dread-only, nothing graphic
- Web JPEGs (~2.5MB total) committed; master PNGs + reference photos gitignored

**What's live / deployed:**
- https://never-broken-site.vercel.app/treatment.html now has: Draft v2 text, Joe's-voice narration, notes, Coach Story widget, and 11 film stills. The full package.

**Next up:**
- Yeti reviews the frames on the live page (swap requests = cheap regens, prompts are in git history)
- Optional: stills grid on index.html playbook page (placeholder slots exist), DeWitt barrier frame, Marcus-brings-a-friend frame
- Send Joe the link

**Notes for other environments:**
- Higgsfield credits after the run: see balance; roughly 15 generations spent this session
- Regen recipe: cinematic_studio_2_5, 21:9, 2k, "prestige drama, 16mm grain" for past / "35mm cool institutional" for present; ALWAYS specify race of every character explicitly or the model whitewashes scenes