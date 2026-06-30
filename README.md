# FindAFrameInterpolation (FAFI)

**FAFI** is a Windows video player with **real-time motion interpolation**. It decodes on
the GPU (Direct3D 11 / D3D11VA hardware decode, zero-copy) and interpolates source frames
up to your monitor's refresh rate — so 24 / 30 / 60 fps material plays back smooth — using
either a fast block-based engine (**MEMC**) or a neural engine (**RIFE**, optional).

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

- **Two interpolation engines, switchable live** — **MEMC** (D3D11 compute-shader motion
  estimation + occlusion-aware synthesis, runs on any modern GPU) and **RIFE** (neural
  intermediate-flow via ncnn-Vulkan; optional, needs a separately obtained model).
- **Hardware decode** (D3D11VA / NVDEC), zero-copy NV12 → RGBA on the GPU.
- **Smooth network streaming** — pick a source quality; short clips can be buffered locally
  first for stutter-free playback, while long videos and live streams start instantly and play
  as they load (with automatic reconnect on drop-outs).
- **Upscaling** — Lanczos-3 with halo-free adaptive sharpening; optional internal 4K target.
- **Image filters** (brightness/contrast/saturation/sharpness/temperature, presets) and a
  **10-band equalizer** with presets.
- **Audio** — WASAPI master clock, device-loss recovery, multi-track, A/V offset, 5.1/7.1.
- **Subtitles** — external `.srt` and `.ass`/`.ssa` (full styling via libass) plus embedded
  text tracks, on a sharp separate layer (never interpolated).
- **Offline export** — render the presented image (interpolation + filters + upscale) to a
  file via an external `ffmpeg`.
- **UI** — slim auto-hiding seekbar and a themed right-click menu holding every control,
  plus an **About** dialog (author, repository, authenticity hint).

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
