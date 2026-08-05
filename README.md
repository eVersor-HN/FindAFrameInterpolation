# FindAFrameInterpolation (FAFI)

*Free, offline-first Windows video player with real-time motion interpolation (MEMC + neural RIFE)
and a reactive music visualiser. No ads, no account, no telemetry — and no features that lock out
when you're offline.*

**FAFI** turns choppy video into **liquid-smooth motion, in real time.** Aim it at **your own
files**, hit play, and 24 / 30 / 60 fps footage flows as fast as your screen can refresh — no ads,
no account, no telemetry, nothing leaving your machine, and **no features that switch themselves off
after you've been offline.** Two engines pull it off: **MEMC** (fast,
always ready) and the optional neural **RIFE** (slower, but razor-clean). Feed it **music instead**
and it flips into a full-screen **reactive light show** that moves to every beat. Web streaming
rides along as a bonus — but the heart of FAFI is your own offline library. Runs fully on the GPU,
so it stays light.

> **Closed-source, proprietary application.** Free to use (including commercially) and to
> share verbatim — **not for sale, not modifiable, no reverse-engineering.**
> See [LICENSE](LICENSE) and [DISCLAIMER](DISCLAIMER.md).

> 💸 You extracted joy and gave nothing back. History's worst people started exactly this small.<br>
> **PayPal:** [paypal.me/FAMarco](https://paypal.me/FAMarco)<br>
> **Bitcoin:** `bc1qv92c3eyeqvhgfnez7spfd7v2aytkhpshsl65yv`

## Local first, private by design

FAFI is built first and foremost as an **offline player for your own video files** — that is
the core, and it works with the network cable pulled. Everything around network streaming
(online video URLs, automatic subtitles) is a **convenience extra on top**, not what the player
is about.

- **No ads. No account. No subscription.** Install it, open a video, done.
- **Never expires, never locks out.** Unlike some players, FAFI **never disables features after a
  stretch offline** — there is no licence check, no online activation, no *"you've been offline too
  long."* Every capability stays unlocked forever, whether you're connected or not.
- **No telemetry, no phone-home:** FAFI sends nothing anywhere. The only network activity
  that ever happens is the one **you** explicitly trigger — opening a stream URL or its
  subtitles, or clicking **Check for updates** in the menu (a one-off request to GitHub —
  never automatic, never on startup). Play local files and FAFI is 100% offline.
  *(No, really — zero. This player has no friends to phone home to.)*
- Transparency note: when you open a streaming URL, FAFI keeps a small local session cookie in
  `%LOCALAPPDATA%\FAFI\cookies.txt` so playback keeps working. It stays on your machine and is
  used for that streaming source only, nowhere else. Delete that file (or set `FAFI_YTDLP_BROWSER=0`) to opt out.

Author / copyright: **© 2026 Marco Aurelio Fattizzo** ([@eVersor-HN](https://github.com/eVersor-HN)).
This is the **official** distribution repository — get FAFI only from here:
**https://github.com/eVersor-HN/FindAFrameInterpolation**

---

## Download & install

1. Open the [**Releases**](https://github.com/eVersor-HN/FindAFrameInterpolation/releases) page
   and download **`FAFI-Setup.exe`** from the latest release.
2. **Verify it is the genuine original** (see below) before running it.
3. Run `FAFI-Setup.exe`. It installs FAFI **per-user** to
   `%LOCALAPPDATA%\Programs\FAFI-Player` (no administrator rights), adds Start-menu / Desktop
   shortcuts and an entry under *Apps & Features* for clean uninstalling.

There is nothing else to install — the player ships with everything it needs.

> 📱 **On a phone?** The same release also carries an **Android APK** — see
> [FAFI for Android](#-fafi-for-android) below.

### Updating

FAFI checks for a new version **only when you ask** (right-click → *Check for updates* — never in
the background, never on startup). When one is available, **one click updates in place**: FAFI
downloads the setup, verifies its checksum, replaces the running player and restarts it — **you
never have to uninstall the old version first.** Prefer to do it by hand? Just run the new
`FAFI-Setup.exe` over your existing install and it updates cleanly, keeping your settings and
shortcuts.

---

## 📱 FAFI for Android

**The same player, on a phone — and the interpolation really runs there.** Not a remote control
for the desktop version and not a skin over the system player: FAFI's own motion interpolation,
its Anime4K upscaling and its screen looks do their work on the handset, on your own files.

- **Comes as an APK you install yourself** — from the same [Releases](https://github.com/eVersor-HN/FindAFrameInterpolation/releases)
  page as the Windows build. **It is not in any app store**, so your phone will ask you to allow
  installing from this source once. Verify its checksum first (see below).
- **Android 10 or newer**, **64-bit ARM only** (`arm64-v8a`) — that is every phone from roughly
  2018 onwards. There is no 32-bit and no x86 build.
- **No internet permission at all.** The app does not request `android.permission.INTERNET`,
  which means the operating system will not let it open a network connection even if something
  in it tried. No ads, no account, no telemetry, no update check, no phoning home — this is not
  a promise in a privacy policy, it is a missing capability you can verify yourself in the app's
  permission list. The flip side is the honest one: **there is no streaming of any kind.** It
  plays files that are on your device, and nothing else.
  *(For completeness, since you will see it in that list: the playback library asks for
  `ACCESS_NETWORK_STATE`, which only lets an app read whether a connection exists. Without
  `INTERNET` it cannot open one.)*
- **The same twelve languages as the Windows player** — it starts in your phone's language and
  can be switched at any time under *Settings → Language*.
- **First release, and it says so.** It plays your own video and music files, does the picture
  work, and has fullscreen, gestures, Picture-in-Picture, background audio with notification
  controls, a history with thumbnails and resume, and folder queues. It does **not** yet have
  subtitles while the FAFI processing is on, or sound-track selection on that path.
  The full and honest list is in
  [**`CHANGELOG-ANDROID.md`**](CHANGELOG-ANDROID.md) — please read it before installing.

Third-party components of the Android app are listed separately, under *Android app*, in
[`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md). The APK contains no FFmpeg and nothing
under the LGPL or GPL; decoding is done by the phone's own media stack.

---

## ✅ Verify authenticity (SHA-256)

Every official release publishes the **SHA-256 checksum** of each downloadable file. Comparing
the checksum of your download against the published value proves the file is the **unmodified
original** and was not tampered with. (The same repository address and this verification hint
are shown inside the Windows app under **right-click → About FAFI**.)

**Windows — v1.15.0 — `FAFI-Setup.exe`:**

```
78fed47a66c37834e1010d8f80257b3e8f757344c00b6978e531ec219032cc4f
```

**Android — v1.15.0 — `FAFI.apk`:**

```
b48a30246694a280b4ae1ef517237429497607bd416e17b9672d565cc93cb8a0
```

The authoritative value for each release is in that release's notes and in its
[`SHA256SUMS.txt`](SHA256SUMS.txt) asset.

**Check it on Windows:**

```powershell
Get-FileHash .\FAFI-Setup.exe -Algorithm SHA256
Get-FileHash .\FAFI.apk       -Algorithm SHA256
```

**Check the APK on a phone or on Linux/macOS:**

```
sha256sum FAFI.apk
```

The printed hash must match the value above (case-insensitive). If it does **not** match, do
**not** run or install the file — it is not the genuine FAFI build.

---

## Features

*Built by one person, fuelled by spite and instant coffee — it shows, mostly in a good way.*

### Smooth motion
- **Two interpolation engines, switchable live (`E`)** — **MEMC** (fast, lightweight, runs on any
  modern GPU) and **RIFE** (neural, razor-clean on hard motion). RIFE **works out of the box** — the
  recommended model is built in (see [RIFE engine](#enabling-the-rife-engine-optional)).
- **A/B compare (`V`)** — a draggable before/after wipe: the plain original on the left, the full
  FAFI treatment on the right. See the difference live.

### Music mode — the room is the show
Feed FAFI an audio file and it stops pretending to be a video player and becomes a **reactive
visualiser**: full-screen, edge to edge, running at your monitor's refresh, moving to every beat,
drop and breath of the track.

- **A whole gallery of live visuals** — from slow drifting fields to hard strobing spectra. Flick
  through them with the arrow keys, or let **shuffle** deal you a fresh one on a timer. Every one of
  them reacts hard and on the beat — no lazy "it wiggles a bit if you squint" filler.
- **Hide the controls and it's just you, the track, and the light** — nothing on screen but the show.
- **Still a player.** Open a file, paste a URL, or drag a video onto the window at any moment and
  FAFI snaps straight back to picture. *Your eyes and your ears take turns; you don't have to choose.*

### Picture
- **HDR playback** — HDR10 / HLG sources are tone-mapped to SDR so bright highlights keep their
  detail on an ordinary display (a couple of looks to choose from); SDR content is untouched.
  Network streams can optionally fetch the HDR version.
- **Upscaling (`L`)** — high-quality upscaling with halo-free sharpening, plus an optional internal
  4K render target (`K`).
- **Correct aspect ratio, automatically** — anamorphic video that older players show **stretched**
  now displays at its true shape without you touching a thing. And when you *want* control, an
  **Aspect ratio** switch offers fit, crop-to-fill (lose the black bars) or stretch.
- **Sideways phone videos play upright** — clips recorded in portrait carry rotation metadata,
  and FAFI honours it automatically: pixel-exact, on the GPU, nothing to configure.
- **Smart picture** — auto-tunes sharpness and colour from the content itself, so most videos look
  right without touching a slider.
- **Image filters (`C`)** — brightness, contrast, saturation, sharpness, colour temperature and
  black point, with presets.
- **Display filters** — optional retro / creative looks over the picture, each with adjustable
  strength: **CRT**, **Aperture Grille**, **Aperture Pure**, **LCD/TFT**, **NTSC**, **35 mm film**,
  **Glitch**, **VHS**, **old handheld**, **E-Paper**, **Dye Transfer**, **StayPlaytion 1**, and a clean
  **Anime Disc** sharpen — plus a **curved-screen** toggle in three flavours: bare tube, tube with
  scanlines and mask, or tube with the stripe mask alone. The menu stays open so you can flick through
  them live. Off by default (zero cost).
- **Antenna** — watching over the air, the way it actually was. The signal drifts on its own: the
  picture is clean for a while, then it sags — the colour fades out to black and white, a ghost of
  the image slides in beside itself, everything softens and flickers with snow, lines tear, a bar
  drifts up the screen. A passing aircraft makes it beat, a fridge or a passing car writes bright
  dashes across it, and now and then lightning wipes a band of it. Then it settles again. Nothing
  loops, nothing repeats — and **Antenna + VHS** puts that reception on tape, the way a home
  recording of a badly received broadcast really looked.
- **Fill the curved screen** — the curved tube bows the picture inwards and used to leave black
  bands top and bottom. The **Tube fill** slider pushes it back out until the edges sit flush
  against your frame, or all the way to the corners for a real television's overscan.
- **In-player ambient light** — a soft, high-quality glow of the picture's own colours spills into
  the black around the video, so your film lights up its own frame with **no LED strip or extra
  hardware**. Fully tunable: how far it reaches (or leave a crisp black border), how soft, how
  bright, how colourful, which sides it lights, and how small the picture floats inside the glow.
  Dial the **border** all the way down and the picture's edge dissolves into its own light — round
  corners, no rectangle, no seam — or keep it at full for a crisp, defined frame.
  Composes with every look — curved tube, retro screens, upscaling — and takes on their colour too.

### Sound
- **Full audio suite** — multi-track selection, A/V offset, correct 5.1 / 7.1 speaker mapping,
  **Smart loudness** (quiet and loud sources sit at an even level), a **virtual surround** downmix
  for headphones, per-ear **balance**, pitch-preserving **tempo**, and preferred-language auto-selection.
- **10-band graphic equalizer (`Q`)** — with presets.
- **Follows your device switch** — plug in a USB DAC or connect Bluetooth headphones and the
  sound moves to the new output immediately, no restart, no silence.

### Subtitles & accessibility
- **Subtitles** — external `.srt` / `.ass` / `.ssa` / `.vtt` (full ASS styling) and embedded tracks,
  on a sharp separate layer that is **never interpolated**. Platform subtitles are fetched
  automatically in your language; drag & drop your own, and nudge the timing (`Ctrl+,` / `Ctrl+.`)
  and position live.
- **Accessibility (Meatware Mods)** — a built-in toolkit for real needs: colour-blind assist modes,
  dialogue boost / mono downmix / amplify for hard-to-hear audio, a flash guard and calmer UI for
  photosensitivity, and pitch-preserving slow-motion that can kick in automatically while subtitles
  are on.

### Formats & streaming
- **Plays virtually any format** — every common codec (H.264, HEVC, VP8/VP9, AV1, MPEG, VC-1, WMV,
  ProRes, DNxHD, …) across all common containers (MP4, MKV, WebM, AVI, MOV, TS, FLV, …), decoded on
  your GPU where possible and in software otherwise — so even AV1 on an older card just plays,
  nothing is left unplayable. Music files (MP3, FLAC, Opus, M4A, WAV, OGG, …) open **instantly** into music mode.
- **View images too** — drop a **PNG, JPG, WebP, BMP or TIFF** onto the window and FAFI shows the
  still picture, with the same zoom and aspect controls as video.
- **Smooth network streaming** — paste a web video link and it just plays: **downloads while
  it plays** (full quality with local-file smoothness), live streams start instantly, drop-outs
  reconnect on their own, and it's **completely ad-free** — no pre-roll, no mid-roll, ever. Recent
  URLs are remembered (`H`).
- **Skip anywhere in a stream** — drag the scrubber to any point in an online video and it jumps
  straight there, forward or back, with no re-loading the whole file and no freezing. Streaming
  scrubs like a local file.
- **SponsorBlock** — flip one switch and community-marked sponsor / self-promo segments in
  supported streams are skipped automatically, with a little note telling you how much you were spared.
- **Members-only streams** — pick which browser's login the player should borrow (*Stream login*
  in the menu) for members-only or age-gated videos; *Auto* finds one on its own.

### Everyday
- **A menu you can drive from the couch** — every control lives in a **honeycomb menu** you open
  with a right-click **or the Escape key**, laid out in tidy categories. It runs **entirely from the
  keyboard**: arrow keys glide between tiles, Space picks, Escape backs out. Multi-choice things
  (filters, EQ, visuals) stay open while you flick through them, so you can hear or see each one and
  change your mind. *No mouse, no squinting, no leaving the sofa.*
- **Your language, 12 of them** — the whole interface is translated into **English, German, French,
  Spanish, Italian, Portuguese, Dutch, Polish, Russian, Turkish, Japanese and Chinese**. Pick one in
  the menu and it sticks.
- **Picture-in-Picture (`P`)** — pop the video out into a small, borderless, always-on-top corner
  window and keep watching while you work.
- **Offline export (`X`)** — render the presented image (interpolation + filters + upscale) to a
  file — one clip, or a **whole folder in batch**; the active subtitle goes along as its own track
  (timing correction baked in) or burned in.
- **Interface themes** — recolour the whole UI and window accent to taste.
- **Profiles** — save your entire setup under a name you type (one for anime, one for retro
  nights, one for the kids …) and switch with a single tap. Device pairings and addresses stay put.
- **Phone remote** — switch on the built-in web remote and open the shown address on your phone
  (same Wi-Fi): play/pause, seek and volume from the couch, no app to install.
- **Real couch input** — media keyboards, Bluetooth remotes and headset buttons just work
  (play/pause, next/previous, volume). `0`–`9` jumps to 0–90%, `Shift+←/→` steps a single frame,
  and a **sleep timer** (30–120 min) quits the player cleanly when you've long stopped watching.
- **"Are you still watching?"** — fall asleep mid-film and the player notices. After the time you
  choose without a single key, click or remote press, it **pauses** so you miss nothing and asks. If
  nobody answers it can stay paused, quit, or **send the PC to sleep / shut it down** — your call.
- **Chapters** — tick marks on the seekbar, hotkeys to jump, and a named chapter list in the menu.
- **Screenshot (`F9`)** — a clean **PNG** of just the picture, your filters and looks included —
  no seekbar or menus baked in.
- **Stats view** — tap `F` twice for a live card: resolution, decode path, true rates, audio
  format, glitch counter, A/V offset.
- **Your room lights follow the film** — drive **WLED** LED strips, **OpenRGB** hardware (Corsair,
  ASUS, Razer, MSI … — every RGB device your PC has), **sACN** receivers, **Razer Chroma** gear,
  **Philips Hue** room lights and **Home Assistant (MQTT)** from the on-screen colour, live. A
  top-down **Light layout** view lets you drag every output — and every single RGB device — to
  where it physically sits around your screen, so each one glows with the colour of *its* side of
  the picture. The first network use asks for your permission first.
- **Repeat & shuffle (`R`)** — off, the current track / video, or the whole folder playlist.
- **Backup & restore** — pack your settings + models, or the whole portable player, into one `.zip`
  and import it on another machine.
- **Update check** — a manual **Check for updates** in the menu. User-triggered only — nothing
  phones home on its own.
- **Reset & remembered settings** — one click restores picture, filters and EQ to defaults; every
  choice is saved and restored across sessions.
- **Clean UI** — a slim auto-hiding seekbar; the title bar and controls fade away when idle, and
  fullscreen (`F11`) is truly borderless.

## Enabling the RIFE engine (optional)

FAFI plays on the default **MEMC** engine out of the box. The neural **RIFE** engine (higher quality
on hard motion) is built in too — **just press `E`**. The recommended model (`rife-v4.22-lite`) is
**embedded in the app**, so the first time you switch to RIFE it sets itself up instantly, offline —
no download, no file juggling. A short **"RIFE active — <model>"** note confirms it's running.

**It even chooses for you:** on a fast **modern GPU** FAFI defaults to RIFE automatically (it's
real-time there); on older cards it stays on MEMC. Your own `E` choice is remembered from then on.

### Want a different model?
FAFI loads any compatible `rife-v4.x` folder you drop into `models\` and **auto-picks the best
present** (order: `v4.22-lite` → `v4.25-lite` → `v4.26` → `v4.25` → `v4.6`, then any other
`rife-v4.*`). Easiest place: **right-click → Interpolation → Open models folder**. Get other models
from [nihui](https://github.com/nihui/rife-ncnn-vulkan) (`rife-v4.6`) or
[TNTwise](https://github.com/TNTwise/rife-ncnn-vulkan) (newer); FAFI picks up whatever you add.

| Model | Quality | Speed¹ | Best for |
|-------|---------|--------|----------|
| **`rife-v4.22-lite`** *(built in)* | sharp; fixes fast-motion warping | balanced | **the default — works out of the box** |
| **`rife-v4.6`** *(download)* | good; softer + more warping | **fastest** | older/weak GPUs wanting max smoothness |
| **`rife-v4.25-lite`** *(download)* | a touch cleaner | slower | maximum quality, speed no object |
| **`rife-v4.25` / `v4.26`** *(download)* | highest | heaviest | strong modern GPUs |

¹ Measured on a high-end 2017-era GPU @1080p. Counter-intuitively the newer nets are **heavier**
(slower), not lighter — on GPUs of that generation `v4.6` stays the fastest, just softer. Only the `rife-v4.x` line
works; the old `rife-v2/v3/anime/HD/UHD` folders use a different network and are ignored.

All `rife-v4.x` model weights are **MIT-licensed** (Practical-RIFE / ECCV2022-RIFE / ncnn — see
[`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md)); using any model is your responsibility (see
[`DISCLAIMER.md`](DISCLAIMER.md)).

## System requirements

- **Windows 10 / 11 (64-bit).**
- A **Direct3D 11** GPU. For the optional RIFE engine, a **Vulkan-capable** GPU/driver.
- *If it won't run, that's a conversation between you and your GPU. Leave me out of it.*
- Optional, for their respective features only: an external `ffmpeg.exe` (export) and
  `yt-dlp` (resolving platform URLs). Neither is bundled.

**Android app:**

- **Android 10** or newer, **64-bit ARM** (`arm64-v8a`) only.
- A phone with **Vulkan** support for the FAFI picture path — every 64-bit device of that
  vintage has it. If yours doesn't get along with it, the app falls back to ordinary playback
  instead of failing.
- Installed by hand from the APK; not distributed through any app store.

## License (summary)

FAFI is **proprietary, closed-source** software under the **FindAFrameInterpolation License**
(full text in [`LICENSE`](LICENSE)):

- ✅ **Use** it for any purpose, **including commercially** (companies may use it).
- ✅ **Share** verbatim, unmodified copies **free of charge**.
- ❌ **No selling** the software, **no modifying / adapting**, **no reverse-engineering,
  decompiling or disassembling** — except where a bundled third-party license requires
  otherwise (the LGPL FFmpeg and FriBidi DLLs stay replaceable; see below).

It bundles third-party components under their own licenses — **FFmpeg** (LGPL-2.1, dynamically
linked, replaceable DLLs), the subtitle stack **libass** (ISC) / **FreeType** (FTL) /
**HarfBuzz** (MIT) / **FriBidi** (LGPL-2.1, replaceable DLL), **ncnn** (BSD-3), the
**rife-ncnn-vulkan** warp layer (MIT), a bundled **QuickJS** (quickjs-ng) JavaScript runtime
(MIT, used by yt-dlp), and permissive support libraries (Brotli, bzip2, libpng, zlib).
Portions of this software are copyright © The FreeType Project (www.freetype.org).
All rights reserved. Full details and texts:
[`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md).

The **Android app** is under the same license but bundles a completely different, much shorter
set of components — the Android platform libraries (Apache-2.0), the Kotlin runtime (Apache-2.0),
the C++ runtime (Apache-2.0 with LLVM Exception) and the **Anime4K** algorithm (MIT). **No FFmpeg,
nothing LGPL or GPL** is in the APK. Its list is the *Android app* section of the same file.

No warranty — see [`DISCLAIMER.md`](DISCLAIMER.md).
