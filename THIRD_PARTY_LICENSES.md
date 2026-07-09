# Third-Party Licenses

FindAFrameInterpolation (FAFI) is distributed under the FindAFrameInterpolation
License (see `LICENSE`). It incorporates the third-party components listed below,
which remain under their own licenses. Nothing in the FindAFrameInterpolation
License removes or restricts any rights or obligations you have under these
licenses.

When you redistribute FAFI in binary form, keep this file and the referenced
license texts alongside the binaries.

**Source code of the LGPL components:** the FFmpeg (8.1.2) and FriBidi (1.0.16)
libraries shipped with FAFI are unmodified builds produced with vcpkg. Their complete
corresponding source code is freely available from the upstream projects
(https://ffmpeg.org/download.html, https://github.com/fribidi/fribidi/releases) and via
the vcpkg registry (https://github.com/microsoft/vcpkg — ports `ffmpeg` 8.1.2 /
`fribidi` 1.0.16). On request, the author will additionally provide a copy of these
sources at no more than the cost of distribution (open an issue at
https://github.com/eVersor-HN/FindAFrameInterpolation/issues); this offer is valid for
three years from the corresponding FAFI release.

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

## libass — subtitle rendering (`ass-9.dll`)
- **License:** ISC.
- **Linking:** dynamic.
- **Source:** https://github.com/libass/libass

```
ISC License

Copyright (C) 2006-2016 libass contributors

Permission to use, copy, modify, and/or distribute this software for any
purpose with or without fee is hereby granted, provided that the above
copyright notice and this permission notice appear in all copies.

THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES
WITH REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF
MERCHANTABILITY AND FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR
ANY SPECIAL, DIRECT, INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES
WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS, WHETHER IN AN
ACTION OF CONTRACT, NEGLIGENCE OR OTHER TORTIOUS ACTION, ARISING OUT OF
OR IN CONNECTION WITH THE USE OR PERFORMANCE OF THIS SOFTWARE.
```

---

## FreeType — font engine (`freetype.dll`)
- **License:** FreeType License (FTL). FreeType is dual-licensed (FTL or GPLv2);
  FAFI uses and redistributes it under the **FTL**, a BSD-style license with a
  credit requirement.
- **Linking:** dynamic (dependency of libass).
- **Required credit:** *Portions of this software are copyright © The FreeType
  Project (www.freetype.org). All rights reserved.*
- **License text:** https://gitlab.freedesktop.org/freetype/freetype/-/blob/master/docs/FTL.TXT
- **Source:** https://freetype.org/

---

## HarfBuzz — text shaping (`harfbuzz.dll`)
- **License:** "Old MIT".
- **Linking:** dynamic (dependency of libass).
- **Source:** https://github.com/harfbuzz/harfbuzz

```
Copyright © 2010-2022  Google, Inc.
Copyright © 2015-2020  Ebrahim Byagowi
Copyright © 2019,2020  Facebook, Inc.
Copyright © 2012,2015  Mozilla Foundation
Copyright © 2011  Codethink Limited
Copyright © 2008,2010  Nokia Corporation and/or its subsidiary(-ies)
Copyright © 2009  Keith Stribley
Copyright © 2011  Martin Hosken and SIL International
Copyright © 2007  Chris Wilson
Copyright © 2005,2006,2020,2021,2022,2023  Behdad Esfahbod
Copyright © 2004,2007,2008,2009,2010,2013,2021,2022,2023  Red Hat, Inc.
Copyright © 1998-2005  David Turner and Werner Lemberg
Copyright © 2016  Igalia S.L.
Copyright © 2022  Matthias Clasen
Copyright © 2018,2021  Khaled Hosny
Copyright © 2018,2019,2020  Adobe, Inc
Copyright © 2013-2015  Alexei Podtelezhnikov

Permission is hereby granted, without written agreement and without
license or royalty fees, to use, copy, modify, and distribute this
software and its documentation for any purpose, provided that the
above copyright notice and the following two paragraphs appear in
all copies of this software.

IN NO EVENT SHALL THE COPYRIGHT HOLDER BE LIABLE TO ANY PARTY FOR
DIRECT, INDIRECT, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES
ARISING OUT OF THE USE OF THIS SOFTWARE AND ITS DOCUMENTATION, EVEN
IF THE COPYRIGHT HOLDER HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH
DAMAGE.

THE COPYRIGHT HOLDER SPECIFICALLY DISCLAIMS ANY WARRANTIES, INCLUDING,
BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND
FITNESS FOR A PARTICULAR PURPOSE.  THE SOFTWARE PROVIDED HEREUNDER IS
ON AN "AS IS" BASIS, AND THE COPYRIGHT HOLDER HAS NO OBLIGATION TO
PROVIDE MAINTENANCE, SUPPORT, UPDATES, ENHANCEMENTS, OR MODIFICATIONS.
```

---

## FriBidi — Unicode bidirectional text (`fribidi-0.dll`)
- **License:** GNU Lesser General Public License (LGPL), version 2.1 or later.
- **Linking:** dynamic (dependency of libass). Shipped as a separate DLL.
- **Your obligations when redistributing FAFI:** the same as for FFmpeg —
  (1) include this notice and the LGPL v2.1 text (bundled as `LGPL-2.1.txt`);
  (2) keep `fribidi-0.dll` a separate, replaceable file — do not statically merge,
  encrypt, or otherwise prevent an end user from substituting their own compatible
  FriBidi build. FAFI does not modify FriBidi.
- **License text:** included as `licenses/LGPL-2.1.txt` (same text as for FFmpeg).
- **Source:** https://github.com/fribidi/fribidi

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

## RIFE flownet model weights (MIT; not part of the installed app)
- The RIFE engine, when enabled, loads a `flownet` model from `models\<name>\` at runtime. A model
  is **not** part of the installed application, and the default MEMC engine works without any model.
- **License: MIT.** The trained `rife-v4.x` weights come from the RIFE research project — hzwer's
  **Practical-RIFE**, whose README states the model downloads are "under the same MIT license as
  this project" (Copyright (c) 2021 hzwer), building on **ECCV2022-RIFE** (Copyright (c) Megvii
  Inc., MIT). The ncnn conversion + runtime and the `rife.Warp` layer are MIT (Copyright (c) nihui).
  Redistribution — including commercially — is therefore permitted, provided the MIT notice is kept.
- Sources: https://github.com/hzwer/Practical-RIFE  /  https://github.com/megvii-research/ECCV2022-RIFE
  /  https://github.com/nihui/rife-ncnn-vulkan  /  https://github.com/TNTwise/rife-ncnn-vulkan
- **Obtaining a model:** download the ncnn `rife-v4.x` model folders from the upstream project —
  https://github.com/TNTwise/rife-ncnn-vulkan (or nihui's original for `rife-v4.6`) — and place one
  into `models\`. **FAFI does not bundle or mirror the model weights**; it only loads whatever you
  put there (and auto-selects the best folder present). If you use a model from another source,
  verify and comply with that model's own terms.

---

## Support libraries — Brotli, bzip2, libpng, zlib

Dynamically linked helper libraries pulled in by FFmpeg and the subtitle stack.
All are permissively licensed; their notices are reproduced below.

### Brotli (`brotlicommon.dll`, `brotlidec.dll`) — MIT
Source: https://github.com/google/brotli

```
Copyright (c) 2009, 2010, 2013-2016 by the Brotli Authors.

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
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.  IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```

### bzip2 / libbzip2 (`bz2.dll`) — bzip2 license (BSD-style)
Source: https://sourceware.org/bzip2/

```
This program, "bzip2", the associated library "libbzip2", and all
documentation, are copyright (C) 1996-2019 Julian R Seward.  All
rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions
are met:

1. Redistributions of source code must retain the above copyright
   notice, this list of conditions and the following disclaimer.

2. The origin of this software must not be misrepresented; you must
   not claim that you wrote the original software.  If you use this
   software in a product, an acknowledgment in the product
   documentation would be appreciated but is not required.

3. Altered source versions must be plainly marked as such, and must
   not be misrepresented as being the original software.

4. The name of the author may not be used to endorse or promote
   products derived from this software without specific prior written
   permission.

THIS SOFTWARE IS PROVIDED BY THE AUTHOR ``AS IS'' AND ANY EXPRESS
OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE
ARE DISCLAIMED.  IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY
DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE
GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS
INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY,
WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING
NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS
SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

Julian Seward, jseward@acm.org
bzip2/libbzip2 version 1.0.8 of 13 July 2019
```

### libpng (`libpng16.dll`) — PNG Reference Library License version 2
Source: http://www.libpng.org/pub/png/libpng.html

```
Copyright (c) 1995-2026 The PNG Reference Library Authors.
Copyright (c) 2018-2026 Cosmin Truta.
Copyright (c) 2000-2002, 2004, 2006-2018 Glenn Randers-Pehrson.
Copyright (c) 1996-1997 Andreas Dilger.
Copyright (c) 1995-1996 Guy Eric Schalnat, Group 42, Inc.

The software is supplied "as is", without warranty of any kind,
express or implied, including, without limitation, the warranties
of merchantability, fitness for a particular purpose, title, and
non-infringement.  In no event shall the Copyright owners, or
anyone distributing the software, be liable for any damages or
other liability, whether in contract, tort or otherwise, arising
from, out of, or in connection with the software, or the use or
other dealings in the software, even if advised of the possibility
of such damage.

Permission is hereby granted to use, copy, modify, and distribute
this software, or portions hereof, for any purpose, without fee,
subject to the following restrictions:

 1. The origin of this software must not be misrepresented; you
    must not claim that you wrote the original software.  If you
    use this software in a product, an acknowledgment in the product
    documentation would be appreciated, but is not required.

 2. Altered source versions must be plainly marked as such, and must
    not be misrepresented as being the original software.

 3. This Copyright notice may not be removed or altered from any
    source or altered source distribution.
```

### zlib (`z.dll`) — zlib license
Source: https://zlib.net/

```
(C) 1995-2026 Jean-loup Gailly and Mark Adler

This software is provided 'as-is', without any express or implied
warranty.  In no event will the authors be held liable for any damages
arising from the use of this software.

Permission is granted to anyone to use this software for any purpose,
including commercial applications, and to alter it and redistribute it
freely, subject to the following restrictions:

1. The origin of this software must not be misrepresented; you must not
   claim that you wrote the original software. If you use this software
   in a product, an acknowledgment in the product documentation would be
   appreciated but is not required.
2. Altered source versions must be plainly marked as such, and must not be
   misrepresented as being the original software.
3. This notice may not be removed or altered from any source distribution.

Jean-loup Gailly        Mark Adler
jloup@gzip.org          madler@alumni.caltech.edu
```

---

## Vulkan runtime / loader
- Provided by the user's GPU driver / Vulkan SDK. Not redistributed with FAFI.

## yt-dlp (optional, external)
- Optional runtime tool used to resolve platform URLs (e.g. YouTube) to a stream URL.
- Invoked as an external process if present on `PATH`; **not bundled** with FAFI.
- yt-dlp is released into the public domain (Unlicense). Source: https://github.com/yt-dlp/yt-dlp

---

## Rajdhani — menu typeface (embedded) — SIL Open Font License 1.1
- **License:** SIL Open Font License, Version 1.1.
- **Bundling:** the `Rajdhani SemiBold` weight, **subset to Latin + punctuation**, is embedded as an
  `RCDATA` resource inside `FindAFrameInterpolation.exe` and loaded at runtime (via
  `AddFontMemResourceEx`) for the aurora-glass right-click menu. Its OFL copyright declares **no
  Reserved Font Name**, so the subset keeps the original family name.
- **Copyright:** Copyright (c) 2014, Indian Type Foundry (info@indiantypefoundry.com).
- **License text:** included as `licenses/OFL-Rajdhani.txt` with binary distributions.
- **Source:** https://github.com/google/fonts/tree/main/ofl/rajdhani

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
