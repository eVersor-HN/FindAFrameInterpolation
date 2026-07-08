# FindAFrameInterpolation (FAFI)

**FAFI** is a Windows video player with **real-time motion interpolation** — built for playing
**your local video files**, offline, with no ads, no account and no data leaving your machine.
It decodes on the GPU (Direct3D 11 / D3D11VA hardware decode, zero-copy) and interpolates source
frames up to your monitor's refresh rate — so 24 / 30 / 60 fps material plays back smooth — using
either a fast block-based engine (**MEMC**) or a neural engine (**RIFE**, optional). Network
streaming is included as a nice extra, but the heart of FAFI is local playback.

> **Closed-source, proprietary application.** Free to use (including commercially) and to
> share verbatim — **not for sale, not modifiable, no reverse-engineering.**
> See [LICENSE](LICENSE) and [DISCLAIMER](DISCLAIMER.md).

> 💸 You extracted joy and gave nothing back. History's worst people started exactly this small: **PayPal [paypal.me/FAMarco](https://paypal.me/FAMarco)**.

## Local first, private by design

FAFI is built first and foremost as an **offline player for your own video files** — that is
the core, and it works with the network cable pulled. Everything around network streaming
(YouTube URLs, automatic subtitles) is a **convenience extra on top**, not what the player
is about.

- **No ads. No account. No subscription.** Install it, open a video, done.
- **No telemetry, no phone-home:** FAFI sends nothing anywhere. The only network activity
  that ever happens is the one **you** explicitly trigger — opening a stream URL (resolved
  and fetched via yt-dlp on your machine) or its subtitles. Play local files and FAFI is
  100% offline. *(No, really — zero. This player has no friends to phone home to.)*
- Transparency note: when you open a YouTube URL, FAFI keeps its own YouTube session
  **locally** in `%LOCALAPPDATA%\FAFI\cookies.txt` to get past YouTube's bot check. It is
  imported **once** from your browser's signed-in cookies (via yt-dlp) and then maintained by
  the player itself — the cookies go to YouTube only, nowhere else, and never leave your
  machine otherwise. Delete that file (or set `FAFI_YTDLP_BROWSER=0`) to opt out.

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

**v1.6.3 — `FAFI-Setup.exe`:**

```
59143ea735e2bf81e45e77b7877d44a050f351f838a9d91840a0d1c05b3cf0d1
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

- **Two interpolation engines, switchable live (`E`)** — **MEMC** (Direct3D 11 compute-shader
  motion estimation + occlusion-aware synthesis; runs on any modern GPU) and **RIFE** (neural
  intermediate-flow via ncnn-Vulkan; optional, needs a separately obtained model — see
  [Enabling the RIFE engine](#enabling-the-rife-engine-optional)).
- **Hardware decode** (D3D11VA / NVDEC), zero-copy NV12 **and 10-bit P010** → RGBA on the GPU.
- **HDR playback** — HDR10 / HLG sources are detected automatically and **tone-mapped to SDR**
  (hue-preserving **Hable** filmic or **Reinhard**, selectable under *Picture → HDR tone
  mapping*), using the stream's real mastering peak and a debanding pass for dark gradients.
  The `F` overlay shows an `HDR→SDR` badge when active; SDR content is untouched. For network
  streams, *Quality → Prefer HDR* optionally fetches the HDR version of a video.
- **Plays virtually any format** — the bundled FFmpeg carries every native decoder (H.264, HEVC,
  VP8/VP9, AV1, MPEG-1/2/4, VC-1, WMV, ProRes, DNxHD, Theora, MJPEG, …) across all common
  containers (MP4, MKV, WebM, AVI, MOV, TS, FLV, …).
- **Smooth network streaming** — platform pages (YouTube, Vimeo, …) resolve via **yt-dlp**; a
  network video **downloads while it plays** (full quality with local-file smoothness), live
  streams start instantly, drop-outs reconnect automatically, and a **progress bar** shows the
  resolve/buffer phases until playback starts. A bundled JavaScript runtime keeps YouTube
  working even without Node/Deno installed.
- **Upscaling** — Lanczos-3 with halo-free adaptive sharpening when the output is larger than the
  source (`L`); optional internal 4K render target (`K`).
- **Image filters** (brightness / contrast / saturation / sharpness / colour temperature + black
  point, presets `C`) and a **10-band graphic equalizer** with presets (`Q`).
- **Smart picture** — auto-tunes sharpness and colour from the content itself (resolution, line-art
  detection, muted-colour boost), so most videos look right without touching a slider.
- **Display filters** — a set of optional looks laid over the picture, each with an adjustable
  strength: **CRT** (scanlines + phosphor shadow mask), **curved CRT** (tube curvature + vignette),
  **Trinitron** (aperture grille), **LCD / TFT** (subpixel grid), animated **VHS Camcorder** (tape
  wobble, chroma bleed, head-switching band), **NTSC Composite** (dot crawl), **Film 35mm** (grain,
  gate weave, warm print), **Glitch**, **Game Boy**, **E-Ink**, **Technicolor** and a clean-master
  **Blu-ray Anime** sharpen. Right-click → *Picture → Display filter* — the menu stays open so you
  can flick through them live. Off by default (zero cost).
- **A/B compare** (`V`) — a draggable before/after wipe: left half the plain original, right
  half the full FAFI treatment (interpolation + filters). See the difference live.
- **Audio** — WASAPI output as the master clock, device-loss recovery, multi-track selection, A/V
  offset, correct 5.1 / 7.1 speaker mapping, **Smart loudness** (transparent auto-gain + soft
  limiter so quiet and loud sources sit at an even level), a **virtual surround** downmix for
  headphones, and preferred-language auto-selection.
- **Subtitles** — external `.srt` and `.ass`/`.ssa` (full styling via libass) plus embedded text
  tracks, on a sharp separate layer that is **never interpolated**.
- **Ambient light / RGB sync** — drive **WLED** LED strips (UDP) and **OpenRGB** devices (TCP) from
  the average on-screen colour for real-time bias lighting.
- **Repeat** — off, repeat the current video, or repeat the whole folder playlist (`R`).
- **Screenshot** (`F9`) — save the exact presented frame (interpolation + filters + upscale) as a BMP.
- **Offline export** — render the *presented* image (interpolation + filters + upscale) to a file
  via an external `ffmpeg` (`X`). The active subtitle goes along as an **own track** (with your
  live timing correction baked in) or **burned into the image** — selectable in the File menu.
- **Reset to defaults** — one menu click restores picture, filters, display filter and audio EQ to
  their defaults (your engine, volume, languages and window preferences are kept). Every setting is
  saved and restored across sessions.
- **UI** — a slim auto-hiding seekbar and a themed **right-click menu** with every setting in
  clean categories (Playback / Quality / Interpolation / Picture / Audio / Subtitles / View /
  File); the title bar and controls fade away together when idle, and fullscreen (`F11`) is
  truly borderless. **About** dialog with author, repository and authenticity hint.

## Enabling the RIFE engine (optional)

The neural **RIFE** engine needs a model (two files: `flownet.param` + `flownet.bin`) that is
**not bundled** with FAFI — the model weights originate from the RIFE research project and may
carry their own terms (possibly non-commercial), so FAFI does not redistribute them. Getting
the model is a one-time, two-minute step:

1. Download a release of the **rife-ncnn-vulkan** project (the ncnn-format models are inside
   the release zip): https://github.com/nihui/rife-ncnn-vulkan/releases — or grab the
   **mirrored, unmodified copy of that zip** attached to the FAFI release page (MIT-licensed;
   its `LICENSE` file is inside the archive).
2. Open the zip and copy the **`rife-v4.6`** folder (it contains `flownet.param` and
   `flownet.bin`) into the player's `models` folder. Easiest way: in FAFI,
   **right-click → Interpolation → Open models folder** — it opens the right place
   (the installer pre-creates it with a README), so it reads:
   ```
   ...\FAFI-Player\models\rife-v4.6\flownet.param
   ...\FAFI-Player\models\rife-v4.6\flownet.bin
   ```
3. Press **`E`** (or *right-click → Interpolation → Engine*) — FAFI picks the model up
   on the fly, **no restart needed**, and switches over as soon as it is loaded.

Without the model FAFI simply keeps using the default MEMC engine. Other RIFE model variants
work too, as long as the folder holds `flownet.param`/`flownet.bin` — put them under
`models\<name>` and select them with the environment variable `FAFI_RIFE_MODEL=<name>`
(faster "lite" variants are a good choice on older GPUs).

> ⚠️ By downloading a model you accept the **model's own license terms** (see the upstream
> project); using it with FAFI is your responsibility — see [`DISCLAIMER.md`](DISCLAIMER.md).

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
