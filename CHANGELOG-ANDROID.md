# What's New in FAFI for Android

Every release, in plain language — what changed for you. Newest first.

**The Android app is experimental** — a side project next to the finished Windows player,
built in the time that is left over. It does real work, and it will have rough edges.

The Windows player keeps its own list in [`CHANGELOG.md`](CHANGELOG.md).

---

## 1.22.0 — 2026-08-15
- **No changes for Android in this version.** It exists so that both products carry the same version
  number: everything in 1.22.0 happened on the Windows player (see [CHANGELOG.md](CHANGELOG.md)).
  The app was rebuilt for this release, so its checksum differs from 1.21.0 even though the code
  behind it is unchanged.
## 1.21.0 — 2026-08-13
- **No changes for Android in this version.** It exists so that both products carry the same version
  number: everything in 1.21.0 happened on the Windows player (see [CHANGELOG.md](CHANGELOG.md)).
  The app was rebuilt for this release, so its checksum differs from 1.20.0 even though the code
  behind it is unchanged.
## 1.20.0 — 2026-08-11
- **No changes for Android in this version.** It exists so that both products carry the same version
  number: everything in 1.20.0 happened on the Windows player (see [`CHANGELOG.md`](CHANGELOG.md)).
  The app was rebuilt for this release, so its checksum differs from 1.19.0 even though the code
  behind it is unchanged.

## 1.19.0 — 2026-08-10
- **No changes for Android in this version.** It exists so that both products carry the same version
  number: everything in 1.19.0 happened on the Windows player (see [`CHANGELOG.md`](CHANGELOG.md)).
  The app is a fresh build of the same code, which is why its checksum differs from 1.18.0 — it
  behaves exactly as it did.

## 1.18.0 — 2026-08-09
- **No changes for Android in this version.** It exists so that both products carry the same version
  number: everything in 1.18.0 happened on the Windows player (see [`CHANGELOG.md`](CHANGELOG.md)).
  The app is a fresh build of the same code, which is why its checksum differs from 1.17.0 — it
  behaves exactly as it did.

## 1.17.0 — 2026-08-08 — 4K stops stuttering, and the picture you made can now leave the phone

- **4K finally plays like everything else.** A ultra-high-definition film could stumble on hardware
  that handles 1080p without breaking a sweat, and the reason turned out to be embarrassing: the
  whole picture chain was doing its work at the resolution of the *file* instead of the resolution
  of your *screen*. On a phone that is four times the effort for pixels nobody can see — and the
  buffers alone were eating hundreds of megabytes. It now works at the size the picture actually
  arrives in, with a proper filter on the way down so brickwork and closing credits do not shimmer.
  Measured on the test phone across four different clips, from 2.5K to 4K, all at sixty frames:
  **a rock-steady 60.00 of 60.00**, where before the first seconds were a mess of missed frames.
- **Export.** The one thing this player could do on the desktop and not on the phone. It writes what
  you are watching into a new file — with the intermediate frames, the picture correction and the
  upscaling baked in, exactly as you see it. The original is never re-encoded and the sound is
  copied across untouched. It survives you leaving the app, shows its progress in a notification,
  and can be stopped there; whatever was written stays playable. *Settings → Export video*, and the
  file lands in `Movies/FAFI`.
- **The output rate is a real limit now.** Setting it below the frame rate of the film used to do
  nothing at all — it only ever capped what the player *added*. Pull it down now and fewer frames
  are shown, which is what you wanted when you pulled it down: less heat, more battery. The film
  does not slow down; individual frames are left out.
- **More frames out of the same phone.** The graphics chip used to sit idle waiting for its turn,
  then sit idle again while the player waited for the next frame's moment to arrive. Those two waits
  are now the same wait. On the clip that pushed the test phone hardest, the peak went from **88 to
  120 frames per second** — the panel's full rate, reached for the first time.
- **Nothing is invented that does not need inventing.** Ask for exactly the frame rate the film
  already has and no intermediate frames are made at all. Give it a film that already has more
  pixels than the screen and the upscaler stays out of it. And a single hiccup in a stream — one
  long gap between frames — no longer convinces the player that the whole film just got slower.
- **Subtitles from a file next to the film.** With FAFI's own engine running there were none at all,
  because that engine only ever decoded picture and sound. `.srt`, `.vtt` and `.ass` files sitting
  beside the video are now read and shown. This needs one thing from you first: *Settings → Share
  folder*. Android does not let an app look into a folder otherwise — and the same permission is
  what makes playing straight through a folder work, which quietly did nothing until now.

## 1.16.0 — 2026-08-05 — it looks like FAFI now, and the picture sits where it should

- **The picture no longer clings to the top of the screen.** With FAFI's own engine running, the
  video could end up squeezed into a band across the top with black everywhere else. The renderer
  was drawing it correctly all along — the surface it was drawn onto had kept the wrong height, and
  the system quietly squashed the result to a quarter. Fixed, and it cannot come back the same way:
  the two halves that disagreed now read the same value.
- **It wears FAFI's face.** The same near-black red ground as the desktop player, the same typeface,
  and the same accent colours — sixteen of them, from Crimson through the whole spectrum to *Ice*,
  the colour-free one with the most contrast. The spread is deliberate: red, green and blue colour
  blindness each keep a shade they can tell apart. *Settings → Colour.*
- **Settings that open a list instead of counting to seventeen.** Anything with more than two
  choices now unfolds where your finger already is, so you can see what is on offer instead of
  tapping through it. Two-value switches stay a single tap.
- **You can reach the settings without opening a video first.** The gear now sits on the start
  screen as well — before, the only one was in the title bar of something already playing.
- **Buttons you can actually hit.** Play/pause was under twenty density-independent pixels wide;
  the guideline is forty-eight. It is seventy-two now, its neighbours fifty-six, and the symbols
  fill them.
- **Extra volume, up to 300 %.** For quiet recordings and for anyone who needs more than the
  system will give. The same look-ahead limiter the desktop player uses holds the peaks, so it gets
  louder without getting coarse. *Settings → Extra volume.*
- **Playback speed, 0.5× to 2×.** For lectures and podcasts. Pitch stays where it belongs.
- **A frame-rate readout, off by default.** It shows what is really being output against the
  source rate — "85.3 fps ← 30" is the interpolation doing its job, and it is the only honest way
  to tell whether it is delivering or has quietly throttled.
- **New screen look: *Black & White TV*.** The same one the desktop player got: broadcast-weighted
  brightness, detail lost along the line and not down the screen, no shadow mask because a
  monochrome tube has none, and a cool blue-white phosphor that blooms around the highlights.
- **The developer entry points are gone from the shipped build**, and the three look sliders
  (strength, scanlines, tube fill) are reachable at last — they existed but nothing led to them.

---

## 1.15.0 — 2026-08-05 — the first Android release

**FAFI's smooth motion and its picture treatment now run on a phone.** Not a remote control for
the desktop player, not a skin over the system player — the same interpolation and the same
upscaling that make FAFI what it is, doing their work on the handset, on your own files, with no
account, no ads and nothing leaving the device.

This is a **first release**, and it is a small app on purpose: it plays your own video and music
files well, and it does the picture work. It does not yet do everything the Windows player does.
The honest list of what is missing is at the bottom — please read it before you install.

### What it does

- **Plays your own files, with two engines.** The everyday engine is the phone's own — fast to
  start, gentle on the battery, and it handles embedded subtitles, multiple sound tracks and the
  notification controls. Alongside it sits **FAFI's own engine**, which is where the interpolation,
  the upscaling and the screen looks live. It is **off until you switch it on** (*Picture → FAFI
  processing*), because it asks a lot more of the phone. Flip it on and FAFI takes over the
  picture; if anything at all goes wrong with a file, the app quietly hands that file back to the
  ordinary engine and keeps playing instead of stopping.
- **Smooth motion, on a phone.** The motion interpolation from the desktop player runs here in
  full: it looks at each pair of frames, works out how everything in the picture moved, and paints
  the frames in between. A 24 fps film stops stepping and starts flowing, as fast as your screen
  can refresh. This is the thing FAFI exists for, and it is the thing most people assume a phone
  cannot do.
- **Anime4K upscaling.** Line art and animation drawn for a small window get their edges pushed
  back together instead of blown up soft. It only engages when the picture is actually being
  enlarged, so it costs nothing when it would do nothing.
- **Sixteen screen looks, and three ways to bend the picture.** CRT, aperture grille, the bare
  stripe mask, LCD/TFT, VHS, NTSC, 35 mm film, glitch, old handheld, e-paper, dye transfer, a
  clean anime sharpen, *StayPlaytion 1*, and over-the-air antenna reception on its own or
  recorded onto tape. Any of them can sit on a flat screen or on a curved tube, with or
  without scanlines. Tap through them live while the film plays. Off by default, and they cost
  nothing when off.
- **Real fullscreen.** The picture goes edge to edge and under the notch. The title bar and the
  controls fade away three seconds after you stop touching anything, and come back with one tap —
  and they stay put while you are paused or have a panel open, instead of vanishing mid-thought.
- **Drive it with your thumb.** Slide up and down on the left for **brightness**, on the right for
  **volume**, sideways anywhere to **scrub** (the picture only jumps when you let go, so a shaky
  thumb costs nothing), and double-tap either half to jump **ten seconds** back or forward. Each
  one shows what it is doing on screen. Don't like any of it? One switch turns the lot off.
- **Picture-in-Picture.** Leave the app and the video shrinks into a corner window and keeps
  playing while you do something else.
- **Music keeps playing when you put the phone down.** Audio carries on in the background with a
  proper notification and lock-screen controls — play, pause, skip — and it survives swiping the
  app away. Headphone and headset buttons work. Unplug the headphones and it pauses instead of
  serenading the bus.
- **Pick up where you left off.** The start screen is a history of what you have watched, each
  entry with a **still from the film itself** and the time you stopped at. Tap it and it resumes
  there. Swipe an entry away to forget it, or clear the lot in one go. Files that have since been
  moved or deleted are shown greyed out rather than failing silently when you tap them.
- **The rest of the folder plays next.** Open one file and FAFI quietly finds its neighbours and
  queues them up, so an evening of episodes or an album plays through without you touching the
  phone again. **Repeat** does nothing, one title, or the whole queue. A file that is broken or
  half-downloaded gets skipped with a note rather than ending the evening — and if three in a row
  fail, FAFI stops and tells you, instead of racing to the end of the folder. **Shuffle** throws the
  order out; switch it off and the folder goes back to the order it had, from wherever you are.
- **A sleep timer that knows about episodes.** Fifteen minutes to an hour and a half — or simply
  *end of title*, which is what you actually mean at midnight. The row counts down while it runs,
  and when the time is up the playback stops where it is and remembers the spot.
- **The screen turns the way you want.** Follow the phone, follow the film's own shape (a portrait
  clip stays portrait, a widescreen film goes landscape), or lock it flat to portrait or landscape.
  The *follow the phone* setting deliberately ignores the system rotation lock, so you can keep
  your home screen locked and still turn a film.
- **It looks like FAFI, not like a stock Android app.** The same near-black red ground, the same
  typeface and the same **fifteen accent colours** as the desktop player — from Deep Scarlet
  through the whole spectrum to *Ice*, the colour-free one with the most contrast. The spread is
  deliberate: red, green and blue colour blindness each keep a shade they can tell apart. Settings
  with more than two values open a list instead of cycling one tap at a time, which matters when
  there are seventeen screen looks to pick from.
- **Twelve languages, same as the desktop player.** English, German, French, Spanish, Italian,
  Portuguese, Dutch, Polish, Russian, Turkish, Japanese and Chinese. It starts in your phone's
  language if that is one of them and in English if it is not, and you can override it at any time
  under *Settings → Language* — the list shows each language in its own script, so you can always
  find your way back out of one you cannot read.
- **Nothing leaves your phone — and it cannot.** The app has **no internet permission at all**.
  That is not a promise in a privacy policy, it is a missing capability: the operating system will
  not let it open a connection even if it wanted to. No ads, no account, no telemetry, no
  check-in, no "you have been offline too long".

### What it costs

Switching FAFI's own engine on means the phone is doing real work on every single frame, and it
asks the screen for its highest refresh rate while it plays. Expect the handset to get warm and
the battery to go down noticeably faster than with ordinary playback. That is the trade, and it is
why the switch starts in the off position. On a long flight, leave it off.

### What this first release cannot do yet

Said plainly, because you should know before you download it:

- **No subtitles when FAFI's own engine is running.** Embedded subtitles work fine on the everyday
  engine, but the moment you switch the FAFI picture processing on, they are gone. Subtitle files
  you supply yourself (`.srt`, `.ass`) are not supported on either engine yet, and there are no
  size, position or timing controls.
- **No sound-track picker when FAFI's own engine is running.** Dual-language files play their
  first track. Switch the processing off and the picker comes back.
- **No streaming of any kind.** No web links, no network shares, no online sources — the app plays
  files that are on the device, and nothing else. This is a deliberate consequence of shipping
  without an internet permission, and it is not coming back later as a surprise.
- **Tested on exactly one phone.** One handset, one graphics chip, one screen. It is worked
  through carefully on that device — and that is a sample of one. On other hardware it may behave
  differently, look wrong, or refuse the FAFI engine entirely (in which case it falls back to
  ordinary playback rather than failing). Treat this release as an invitation to tell me what
  happened on yours.
- **The sleep timer ends if you swipe the app away.** Send FAFI to the background and the timer
  keeps running, which is the case it is for. Swipe the app out of the recent-apps list while music
  carries on and the timer goes with it, and the music does not stop by itself.
- **Also not here yet:** playback speed, the equaliser and the rest of the sound suite,
  zoom and crop controls, chapters, and screenshots. The settings are a plain list rather than
  the desktop player's honeycomb — everything that lives in those tiles is a normal setting here,
  which on a phone is the better shape anyway.

---

*Found something broken, or something that works beautifully? Say so — this one especially needs
to be tried on hardware I do not own.*
