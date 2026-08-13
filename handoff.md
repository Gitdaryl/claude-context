## Session: Aug 12 2026 ET
**Environment:** Antigravity IDE

**What was done:**
- Audited what is actually connected: Higgsfield is an MCP connector; Kie.ai is a raw REST key (not MCP); Krea has a skill installed but no KREA_API_TOKEN, so it is not connected at all.
- Ran a real A/B cost test instead of trusting price pages. Same reference image, same prompt, same 5s clip on both platforms, measured by credit-balance delta.
  - Higgsfield Kling 3.0 pro (sound off): 7.5 credits
  - Kie.ai Kling 2.1 pro: 50 credits = $0.25
- Found Kie's catalog tops out at Kling 2.5, so it has no Kling 3.0 at any price.
- Kie's Kling 2.1 failed the palette: washed the steel raven orange and changed its material by second 3. Kling 3.0 held cold steel for the full 5s.
- Solved the letter-placement problem for the Excitement Software raven concept: never let the model render letters. Composite sprites from the existing EXCITEMENT ASSEMBLED.png, and crossfade to EXCITEMENT BACKLIT.png for the backlight beat. Both files already exist, so those beats cost zero credits.

**What's live / deployed:**
- Nothing deployed. Test clips and a frame comparison saved to ~/Projects/excitement-software/tests/ (raven-place-higgsfield-kling30.mp4, raven-place-kie-kling21.mp4, raven-place-COMPARE.png).
- PRODUCTION.md updated with the measured cost table and the letter-placement architecture.

**Next up:**
- Generate the remaining three raven clips (perch idle, settle, takeoff) on Kling 3.0 to match the dip-and-reach test.
- Cut the 10 letter sprites from EXCITEMENT ASSEMBLED.png.
- Wire the sequence into the scroll engine alongside the existing c/raven build.
- Higgsfield balance is low (320 credits). Worth checking the actual plan charge to work out cost per credit, which is the only number that decides the Kie question.

**Notes for other environments:**
- Krea will fail on first call until KREA_API_TOKEN is set. The skill is installed, the access is not.
- Rule of thumb going forward: Kie for throwaway volume on stock models, Higgsfield for anything that gets graded or needs character/product consistency.