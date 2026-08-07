## Session: 2026-08-07 (ET)
**Environment:** Antigravity IDE
**Project:** Excitement Software (Dave Werner incubator brand)

**What was done:**
- Built scroll-scrub concept site from scratch at ~/Projects/excitement-software (vanilla HTML/CSS/canvas, no deps)
- Concept: "Excitement is manufactured here" — the holding co as a factory, companies as units on a production line, empty carriers = open slots
- Three acts: Trailer (0-74%) → The Record (74-93%) → Mark + Gate (93-100%)
- Instrument/HUD layer: telemetry (CHG/TMP/PSI/VEL/STN/SYS/CTL), altimeter tape, counter-rotating scope rings, world-locked target lock-on that snaps to each carrier (UNIT 01 / STATUS: LIVE, SLOT 06 / STATUS: OPEN)
- Orbital particle swarm on an ambient clock (machine breathes; story stays scroll-locked)
- Mobile pass: 13.9fps → 43.8fps (baked gradient sprites, DPR cap 1.5, halved particles, killed blend-mode overlay); fixed address-bar timeline jump (fixed-px runway denominator); portrait reframing
- Autoplay with gravity resume per Dave: any input cuts the motor dead, eases back after 2.6s idle. CTL row shows AUTO/MANUAL. Suppressed under prefers-reduced-motion
- Cold open sped up: motion instant, headline readable ~1.0s, chamber at 2.1s (launch multiplier decays to cruise; manual scrub unchanged)
- Haptics wired (navigator.vibrate) — works Android, NOT iOS Safari (no Vibration API). Visual bracket punch carries the snap on all devices
- Wrote CONCEPT.md: concept, psychology (split established research vs craft judgement), the CTA-warrant gap and its fix, 7 asks for Dave
- Drafted Slack messages for Dave + 10 doctrine questions

**What's live / deployed:**
- https://excitement-software.vercel.app (Vercel, aliased). noindex. CONCEPT / NOT FOR DISTRIBUTION stamp.

**Next up:**
- Yeti reviewing the cold-open pacing (launch multiplier may need pulling back if too brisk)
- Blocked on Dave: verified record facts, ENTRY 03 (the Matt Mullenweg / WordPress claim — left as a deliberately empty field, needs a name + source or gets cut), what sits behind REQUEST ACCESS, the doctrine, the ask
- Footage swap: architecture already supports a frame sequence via CONFIG.frameCount, currently 0 (procedural placeholder)
- Higgsfield credits at 608 — enough for ~10-15 Kling shots, no iteration room. Flag before generating.

**Notes for other environments:**
- Kling 3.0 beats Seedance 2 for non-human/mechanical elements (Yeti's experience, matches the containment-prompt memory)
- Repo is local only, not yet pushed to GitHub