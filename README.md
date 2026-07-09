# FindAFrameInterpolation (FAFI)

**FAFI** turns choppy video into **liquid-smooth motion, in real time.** Aim it at **your own
files**, hit play, and 24 / 30 / 60 fps footage flows as fast as your screen can refresh — no ads,
no account, no telemetry, nothing leaving your machine. Two engines pull it off: **MEMC** (fast,
always ready) and the optional neural **RIFE** (slower, but razor-clean). Web streaming rides along
as a bonus — but the heart of FAFI is your own offline library. Runs fully on the GPU, so it stays light.

> **Closed-source, proprietary application.** Free to use (including commercially) and to
> share verbatim — **not for sale, not modifiable, no reverse-engineering.**
> See [LICENSE](LICENSE) and [DISCLAIMER](DISCLAIMER.md).

> 💸 You extracted joy and gave nothing back. History's worst people started exactly this small: **PayPal [paypal.me/FAMarco](https://paypal.me/FAMarco)** · **Bitcoin** `bc1qv92c3eyeqvhgfnez7spfd7v2aytkhpshsl65yv`.

## Local first, private by design

FAFI is built first and foremost as an **offline player for your own video files** — that is
the core, and it works with the network cable pulled. Everything around network streaming
(online video URLs, automatic subtitles) is a **convenience extra on top**, not what the player
is about.

- **No ads. No account. No subscription.** Install it, open a video, done.
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

---

## ✅ Verify authenticity (SHA-256)

Every official release publishes the **SHA-256 checksum** of `FAFI-Setup.exe`. Comparing the
checksum of your download against the published value proves the file is the **unmodified
original** and was not tampered with. (The same repository address and this verification hint
are shown inside the app under **right-click → About FAFI**.)

**v1.7.0 — `FAFI-Setup.exe`:**

```
a9e27c16eafd21786066e6d09056aac40e1625e8610ad3fcff0c07c9cdcb707a
```

The authoritative value for each release is in that release's notes and in its
[`SHA256SUMS.txt`](SHA256SUMS.txt) asset.

**Check it on Windows:**

```powershell
Get-FileHash .\FAFI-Setup.exe -Algorithm SHA256
```

The printed hash must match the value above (case-insensitive). If it does **not** match, do
**not** run the file — it is not the genuine FAFI build.

---

## Features

*Built by one person, fuelled by spite and instant coffee — it shows, mostly in a good way.*

### Smooth motion
- **Two interpolation engines, switchable live (`E`)** — **MEMC** (fast, lightweight, runs on any
  modern GPU) and **RIFE** (neural, razor-clean on hard motion). RIFE **works out of the box** — the
  recommended model is built in (see [RIFE engine](#enabling-the-rife-engine-optional)).
- **A/B compare (`V`)** — a draggable before/after wipe: the plain original on the left, the full
  FAFI treatment on the right. See the difference live.

### Picture
- **HDR playback** — HDR10 / HLG sources are tone-mapped to SDR so bright highlights keep their
  detail on an ordinary display (a couple of looks to choose from); SDR content is untouched.
  Network streams can optionally fetch the HDR version.
- **Upscaling (`L`)** — high-quality upscaling with halo-free sharpening, plus an optional internal
  4K render target (`K`).
- **Smart picture** — auto-tunes sharpness and colour from the content itself, so most videos look
  right without touching a slider.
- **Image filters (`C`)** — brightness, contrast, saturation, sharpness, colour temperature and
  black point, with presets.
- **Display filters** — optional retro / creative looks over the picture, each with adjustable
  strength: **CRT**, **Trinitron**, **LCD/TFT**, **NTSC**, **35 mm film**, **Glitch**, **old
  handheld**, **E-Ink**, **Technicolor**, **StayPlaytion 1**, and a clean **Blu-ray Anime** sharpen —
  plus a **curved-screen** toggle. The menu stays open so you can flick through them live. Off by
  default (zero cost).

### Sound
- **Full audio suite** — multi-track selection, A/V offset, correct 5.1 / 7.1 speaker mapping,
  **Smart loudness** (quiet and loud sources sit at an even level), a **virtual surround** downmix
  for headphones, and preferred-language auto-selection.
- **10-band graphic equalizer (`Q`)** — with presets.

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
  your GPU.
- **Smooth network streaming** — paste a web video link and it just plays: **downloads while
  it plays** (full quality with local-file smoothness), live streams start instantly, drop-outs
  reconnect on their own, and it's **completely ad-free** — no pre-roll, no mid-roll, ever. Recent
  URLs are remembered (`H`).

### Everyday
- **Offline export (`X`)** — render the presented image (interpolation + filters + upscale) to a
  file; the active subtitle goes along as its own track (timing correction baked in) or burned in.
- **Screenshot (`F9`)** — save the exact presented frame.
- **Ambient light / RGB sync** — drive **WLED** strips and **OpenRGB** devices from the average
  on-screen colour for real-time bias lighting.
- **Repeat (`R`)** — off, the current video, or the whole folder playlist.
- **Backup & restore** — pack your settings + models, or the whole portable player, into one `.zip`
  and import it on another machine.
- **Update check** — a manual **Check for updates** in the menu. User-triggered only — nothing
  phones home on its own.
- **Reset & remembered settings** — one click restores picture, filters and EQ to defaults; every
  choice is saved and restored across sessions.
- **Clean UI** — a slim auto-hiding seekbar and a themed **right-click menu** with every control in
  tidy categories; the title bar and controls fade away when idle, and fullscreen (`F11`) is truly
  borderless.

## Enabling the RIFE engine (optional)

FAFI plays on the default **MEMC** engine out of the box. The neural **RIFE** engine (higher quality
on hard motion) is built in too — **just press `E`**. The recommended model (`rife-v4.22-lite`) is
**embedded in the app**, so the first time you switch to RIFE it sets itself up instantly, offline —
no download, no file juggling. A short **"RIFE active — <model>"** note confirms it's running.

**It even chooses for you:** on a fast **RTX-class GPU** FAFI defaults to RIFE automatically (it's
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
| **`rife-v4.25` / `v4.26`** *(download)* | highest | heaviest | strong RTX-class GPUs |

¹ Measured on a GTX 1080 Ti @1080p. Counter-intuitively the newer nets are **heavier** (slower),
not lighter — on Pascal-class GPUs `v4.6` stays the fastest, just softer. Only the `rife-v4.x` line
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

No warranty — see [`DISCLAIMER.md`](DISCLAIMER.md).
