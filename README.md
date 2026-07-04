# FindAFrameInterpolation (FAFI)

**FAFI** is a Windows video player with **real-time motion interpolation**. It decodes on the
GPU (Direct3D 11 / D3D11VA hardware decode, zero-copy) and interpolates source frames up to your
monitor's refresh rate — so 24 / 30 / 60 fps material plays back smooth — using either a fast
block-based engine (**MEMC**) or a neural engine (**RIFE**, optional).

> **Closed-source, proprietary application.** Free to use (including commercially) and to
> share verbatim — **not for sale, not modifiable, no reverse-engineering.**
> See [LICENSE](LICENSE) and [DISCLAIMER](DISCLAIMER.md).

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

**v1.1 — `FAFI-Setup.exe`:**

```
337a9f2d761f55b68028558ef3f73bafe30114ea0ce6222054a5341167a120d2
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

- **Two interpolation engines, switchable live (`E`)** — **MEMC** (Direct3D 11 compute-shader
  motion estimation + occlusion-aware synthesis; runs on any modern GPU) and **RIFE** (neural
  intermediate-flow via ncnn-Vulkan; optional, needs a separately obtained model).
- **Hardware decode** (D3D11VA / NVDEC), zero-copy NV12 → RGBA on the GPU.
- **Plays virtually any format** — the bundled FFmpeg carries every native decoder (H.264, HEVC,
  VP8/VP9, AV1, MPEG-1/2/4, VC-1, WMV, ProRes, DNxHD, Theora, MJPEG, …) across all common
  containers (MP4, MKV, WebM, AVI, MOV, TS, FLV, …).
- **Smooth network streaming** — platform pages (YouTube, Vimeo, …) resolve via **yt-dlp**; a
  network video **downloads while it plays** (full quality with local-file smoothness), live
  streams start instantly, and drop-outs reconnect automatically. A bundled JavaScript runtime
  keeps YouTube working even without Node/Deno installed.
- **Upscaling** — Lanczos-3 with halo-free adaptive sharpening when the output is larger than the
  source (`L`); optional internal 4K render target (`K`).
- **Image filters** (brightness / contrast / saturation / sharpness / colour temperature, presets
  `C`) and a **10-band graphic equalizer** with presets (`Q`).
- **Audio** — WASAPI output as the master clock, device-loss recovery, multi-track selection, A/V
  offset, correct 5.1 / 7.1 speaker mapping.
- **Subtitles** — external `.srt` and `.ass`/`.ssa` (full styling via libass) plus embedded text
  tracks, on a sharp separate layer that is **never interpolated**.
- **Repeat** — off, repeat the current video, or repeat the whole folder playlist (`R`).
- **Offline export** — render the *presented* image (interpolation + filters + upscale) to a file
  via an external `ffmpeg` (`X`).
- **UI** — a slim auto-hiding seekbar and a themed **right-click menu** holding every control; the
  title bar and controls fade away together when idle, and fullscreen (`F11`) is truly borderless.
  **About** dialog with author, repository and authenticity hint.

## System requirements

- **Windows 10 / 11 (64-bit).**
- A **Direct3D 11** GPU. For the optional RIFE engine, a **Vulkan-capable** GPU/driver.
- Optional, for their respective features only: an external `ffmpeg.exe` (export) and
  `yt-dlp` (resolving platform URLs). Neither is bundled.

## License (summary)

FAFI is **proprietary, closed-source** software under the **FindAFrameInterpolation License**
(full text in [`LICENSE`](LICENSE)):

- ✅ **Use** it for any purpose, **including commercially** (companies may use it).
- ✅ **Share** verbatim, unmodified copies **free of charge**.
- ❌ **No selling** the software, **no modifying / adapting**, **no reverse-engineering,
  decompiling or disassembling** — except where a bundled third-party license requires
  otherwise (the LGPL FFmpeg DLLs stay replaceable; see below).

It bundles third-party components under their own licenses — **FFmpeg** (LGPL-2.1, dynamically
linked, replaceable DLLs), **ncnn** (BSD-3) and the **rife-ncnn-vulkan** warp layer (MIT).
Full details and texts: [`THIRD_PARTY_LICENSES.md`](THIRD_PARTY_LICENSES.md).

No warranty — see [`DISCLAIMER.md`](DISCLAIMER.md).
