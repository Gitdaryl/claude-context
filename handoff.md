## Session: 2026-11-21 ET
**Environment:** Antigravity IDE
**What was done:**
- Analysed `~/Downloads/what is this song.mp4` (IG download, 2:58, AI fashion visuals) to write a Suno style prompt. Song not identified by name; no recognition service was used.
- Measured locally (librosa, demucs stems, CLAP tagger via `uv run`): 112 BPM, D minor with harmonic-minor colour, straight four-on-the-floor kick, sub-heavy synth bass on D / G / B flat, female talk-rap around D4, beatless spoken intro for the first 30 s, chorus at 1:24.
- Suno style prompt (short): Midtempo runway house, 112 BPM, D harmonic minor, four-on-the-floor kick, rubbery sub synth bass, sparse dark beat, sassy female talk-rap, sultry, glamorous, vintage reed hook, clean modern mix

**What's live / deployed:**
- Nothing.

**Next up:**
- None owed. Yeti to try the prompt in Suno; the "vintage reed hook" phrase is the least certain part and the first thing to drop or swap.

**Notes for other environments:**
- Local audio analysis works on this Mac with no installs: `uv run --python 3.11 --with librosa` for tempo/key, `--with torch==2.5.1 --with torchaudio==2.5.1 --with demucs` for stems, `--with transformers==4.44.2` plus `laion/larger_clap_music_and_speech` for zero-shot tagging, `--with faster-whisper` for lyrics.