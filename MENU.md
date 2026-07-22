# FAFI — Menu map

Everything in FAFI lives in **one right-click menu** — right-click anywhere on the video
(or the window) to open it. Letters in `(brackets)` are keyboard shortcuts that do the same
thing without opening the menu.

The menu **stays open while you toggle settings**, so you can flick through options and see
the effect live.

```text
Right-click menu
│  Interpolation on/off (I)  ·  Engine: MEMC ↔ RIFE (E)     ← the two main toggles, up top
│  Play / Pause (Space)
│
├─ Source
│    Open file (O) · Load URL (U) · Recent URLs / History (H)
│    Export video (X) · Export subtitles
│    Repeat (R) · Previous / Next (N) · Playlist
│
├─ Picture
│    Smart picture
│    ── SCALING ──  Upscaling (L) — Auto / FSR / Anime4K · Supersample (K)
│    ── TONE ──  HDR tone mapping · Black point (B) · Colour tuner (C) · A/B compare (V)
│
├─ FX & Lights
│    Screen look — CRT / NTSC / 35 mm film / Glitch / old handheld / … · Look strength · Curved screen
│    Ambient light (WLED) · RGB sync (OpenRGB)
│
├─ Sound
│    Smart loudness · Mute (M) · Audio track (A) · Virtual surround · Equalizer (Q)
│
├─ Subtitles (S)
│    Off / pick a track · Load subtitle file · Timing (Ctrl+, / Ctrl+.) · Position & size
│
├─ Screen
│    Fullscreen (F11) · Picture-in-Picture (P) · Always on top (T) · Single window · FPS overlay (F)
│
├─ Meatware Mods   (accessibility)
│    Vision — colour-blind correction, low-vision boost
│    Hearing — dialogue boost, mono downmix, volume boost
│    Photosensitivity — flash guard, calmer UI
│    Reading & speed — pitch-preserving slow-motion, auto-slow on subtitles, subtitle hold
│
└─ Advanced
     Anti-smear (line art) · Frame-rate cap · Open models folder
     Stream quality   ⚠ appears only while a stream / URL is playing
     Backup & restore · Keyboard shortcuts
```

**Two kinds of "look" settings, kept clearly apart:**

- **Colour tuner** (Picture) — the *correction* controls: brightness, contrast, saturation,
  sharpness, warmth. Makes the picture look **right**.
- **Screen look** (FX & Lights) — the *creative* filters: CRT, NTSC, 35 mm film, glitch, and
  other retro looks. Makes the picture look **like something**.

> **Can't find the streaming settings?** The **Stream quality** entry — resolution, buffering,
> and HDR preference — only appears **while a stream is open**, under **Advanced → Stream quality**.
> With a local file there's nothing to set there, so it stays hidden.
