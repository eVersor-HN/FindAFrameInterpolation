# Third-Party Licenses

FindAFrameInterpolation (FAFI) is distributed under the FindAFrameInterpolation
License (see `LICENSE`). It incorporates the third-party components listed below,
which remain under their own licenses. Nothing in the FindAFrameInterpolation
License removes or restricts any rights or obligations you have under these
licenses.

When you redistribute FAFI in binary form, keep this file and the referenced
license texts alongside the binaries.

---

## FFmpeg — libavcodec, libavformat, libavutil, libswscale, libswresample
- **License:** GNU Lesser General Public License (LGPL), version 2.1.
- **Linking:** dynamic. Shipped as separate DLLs (`avcodec-*.dll`, `avformat-*.dll`,
  `avutil-*.dll`, `swscale-*.dll`, `swresample-*.dll`).
- **Build:** this build uses **only** the avcodec/avformat/avutil/swscale/swresample
  components with **no GPL-licensed features** (no `--enable-gpl`, no x264/x265), so
  the FFmpeg libraries here are LGPL, not GPL.
- **Your obligations when redistributing FAFI:** (1) include this notice and the LGPL
  v2.1 text; (2) keep the FFmpeg DLLs as separate, replaceable files — do not statically
  merge, encrypt, or otherwise prevent an end user from substituting their own compatible
  FFmpeg build. FAFI does not modify FFmpeg.
- **License text:** https://www.gnu.org/licenses/old-licenses/lgpl-2.1.html
  (include a copy as `licenses/LGPL-2.1.txt` with binary distributions).
- **Source:** https://ffmpeg.org/

> Note: the optional **video export** feature invokes a *separate, user-provided*
> `ffmpeg.exe` as an external process. That executable is not part of FAFI, is not
> bundled, and is governed entirely by its own license (which may differ, e.g. GPL if
> the user installed a GPL build). FAFI imposes no terms on it.

---

## ncnn (Tencent)
- **License:** BSD 3-Clause.
- **Linking:** dynamic (`ncnn.dll`). Used for the RIFE neural-inference path (Vulkan).
- **Source:** https://github.com/Tencent/ncnn

```
Copyright (c) 2017 THL A29 Limited, a Tencent company. All rights reserved.

Redistribution and use in source and binary forms, with or without modification,
are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list
   of conditions and the following disclaimer.
2. Redistributions in binary form must reproduce the above copyright notice, this list
   of conditions and the following disclaimer in the documentation and/or other
   materials provided with the distribution.
3. Neither the name of the copyright holder nor the names of its contributors may be
   used to endorse or promote products derived from this software without specific
   prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY
EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL
THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT
OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION)
HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR
TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
```

> ncnn statically bundles some permissively licensed build-time components (e.g. SPIR-V
> tooling, glslang under Apache-2.0/BSD/MIT). They are covered by their respective
> permissive licenses; see the ncnn repository for details.

---

## rife-ncnn-vulkan — Warp compute layer (`third_party/rife/`)
- **License:** MIT (Copyright (c) nihui).
- **Linking:** compiled into `FindAFrameInterpolation.exe`. This is the custom `rife.Warp`
  compute layer required by the RIFE engine.
- **Source:** https://github.com/nihui/rife-ncnn-vulkan

```
MIT License

Copyright (c) 2021 nihui

Permission is hereby granted, free of charge, to any person obtaining a copy of this
software and associated documentation files (the "Software"), to deal in the Software
without restriction, including without limitation the rights to use, copy, modify, merge,
publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons
to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or
substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED,
INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR
PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE
FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.
```

---

## RIFE flownet model weights (NOT bundled)
- The RIFE engine, when enabled, loads a `flownet` model (e.g. `rife-v4.6`) at runtime.
- **These model weights are NOT distributed with FAFI** and are not part of this
  repository. The RIFE engine is optional; the default MEMC interpolation engine works
  without any model.
- The trained weights originate from the RIFE project (Huang et al., "Real-Time
  Intermediate Flow Estimation for Video Frame Interpolation"). The *training/inference
  code* is MIT-licensed, but the *model weights* may carry separate terms (including
  possible non-commercial or redistribution restrictions).
- **If you choose to obtain and use a RIFE model, verify and comply with its terms with
  the upstream project.** Do not redistribute the weights through FAFI unless their
  license permits it.
- Sources: https://github.com/hzwer/Practical-RIFE  /  https://github.com/megvii-research/ECCV2022-RIFE

---

## Vulkan runtime / loader
- Provided by the user's GPU driver / Vulkan SDK. Not redistributed with FAFI.

## yt-dlp (optional, external)
- Optional runtime tool used to resolve platform URLs (e.g. YouTube) to a stream URL.
- Invoked as an external process if present on `PATH`; **not bundled** with FAFI.
- yt-dlp is released into the public domain (Unlicense). Source: https://github.com/yt-dlp/yt-dlp

---

## QuickJS (quickjs-ng) — bundled JavaScript runtime (`qjs.exe`)
- **License:** MIT.
- **Bundling:** shipped as a standalone `qjs.exe` next to the player. It is used only as yt-dlp's
  JavaScript runtime (to solve YouTube's "n" signature) on machines that have neither Node.js nor
  Deno installed. FAFI does not link against it; it is launched by yt-dlp as an external process.
- **Source / build:** https://github.com/quickjs-ng/quickjs (release v0.15.1, `qjs-windows-x86_64.exe`).

```
The MIT License (MIT)

Copyright (c) 2017-2026 Fabrice Bellard
Copyright (c) 2017-2024 Charlie Gordon
Copyright (c) 2023-2026 Ben Noordhuis
Copyright (c) 2023-2026 Saúl Ibarra Corretgé

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL
THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
