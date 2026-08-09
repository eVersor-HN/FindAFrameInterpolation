# What's New in FAFI

Every release, in plain language — what changed for you. Newest first.

---

## 1.18.0 — 2026-08-09
- **Export finally has a menu.** Everything the export does — the frame rate it renders at, whether
  it lifts the picture to 4K, whether the neural upscaler runs, H.264 or HEVC, 8-bit or 10-bit,
  what happens to the subtitles — was previously reachable only by setting environment variables
  before launching the player. Which meant, in practice, that nobody could reach it. It now has its
  own page in the honeycomb menu, sitting next to the button that starts the job, and every choice
  survives a restart. The 10-bit switch pulls the codec along with it, because ten bits only exist
  as HEVC and an option that quietly does nothing is worse than no option.
- **Six settings that could not be operated at all.** Deep in the code that turns a menu click into
  an action, one test swallowed every command above a certain number and stopped there. Everything
  written after it was unreachable, and nobody had noticed which features that was: **jumping to a
  chapter, the sleep timer, saved profiles, the "are you still watching?" prompt and the phone
  remote**. All of them are live again. If you ever set one of these and it did nothing, that was
  this, and it was not your fault.
- **The menu text now fills the tile.** Labels were drawn at a fixed size, so a short word left half
  the hexagon empty while a long translation had to squeeze. Every label on a page is now measured,
  and the page draws at the largest size where they all still fit — bigger, and still perfectly even
  across every tile, in all twelve languages. Values are no longer cut off after fifteen characters
  either, which used to slice words in half in German and Russian.

## 1.17.0 — 2026-08-08
- **No changes for Windows in this version.** It exists so that both products carry the same
  version number: everything in 1.17.0 happened on the phone (see
  [`CHANGELOG-ANDROID.md`](CHANGELOG-ANDROID.md)). The installer is a fresh build of the same
  code, which is why its checksum differs from 1.16.0 — the player itself behaves exactly as
  it did.

## 1.16.0 — 2026-08-05
- **Turn it up to 300 % without it turning ugly.** The *Amplify* slider always went to 300 %, but the way it got there was a shortcut: every sample was bent through a curve, which made quiet material louder and loud material coarse. On a one-kilohertz tone at -6 dBFS that measured **11.8 % distortion**, and at full scale **25.7 %** — audible as grit on anything modern and loud. It now runs through a proper look-ahead limiter: the loudest peak still to come is known before it arrives, so the level is already pulled back when it gets there and nothing is bent that does not have to be. Same tone, same 300 %: **0.000 %**. Below the point where it starts working the signal is passed through untouched, bit for bit, and a single bang no longer ducks the quiet passage behind it.
- **New screen look: *Black & White TV*.** Not a colour picture with the colour turned off — a monochrome set was a different machine. The broadcast carried brightness only, so the colours are weighed the way the transmitter weighed them (which is why lipstick reads black, exactly as it did in 1965). Detail is lost **along** the line and not down the screen, because that is what the narrower bandwidth did. There is no shadow mask, because a monochrome tube has one continuous coating and nothing to divide it. And the phosphor is a cool blue-white that blooms around bright areas through the thick safety glass — that glow is what makes it look lit rather than printed. Add the curved tube on top for the full living-room set.
- **The ambient glow now reaches every edge at the same time.** With a widescreen film, shrinking the picture used to fill the glow to the top and bottom long before it got near the left and right. That was geometry, not taste: one reach was measured for both directions, and the way to the top edge is barely half the way to the side. Each direction is now measured against the room it actually has, so at 100 % the light arrives everywhere at once — whatever the window shape and whatever the film. The old behaviour is one switch away (*AMBIENT → Even reach*).
- **The *Illegal Stuff* easter egg runs smoothly again.** It was the only piece of interface animation still tied to the video frame-rate cap, so with a cap set the flying window and the verdict that slams onto the screen stuttered. It now gets the same 60 fps every menu does. Nothing about it takes longer — it just moves properly.

## 1.15.0 — 2026-08-05
- **The screen masks are finally visible.** Every look built on a phosphor mask — *CRT*, *Curved CRT*, *Aperture Grille*, *LCD/TFT*, the console look's dither, the faint broadcast lines in *NTSC* and *Film 35mm* — drew its horizontal half at exactly one screen pixel per line. At that size the pattern landed on the same value in every single pixel and cancelled itself out completely: you got the colour tint and the vignette, but not the woven texture that makes a picture read as a real tube. The mask is now drawn at a size the eye can actually resolve, and all of those looks show the structure they were always meant to have. If you have used them before, they will look noticeably different — and considerably more like the thing they imitate.
- **New screen look: *Aperture Pure*.** The stripe mask on its own: fine vertical lines of red, green and blue, with nothing laid across them. The trick of the tubes that never had a shadow mask — continuous wires top to bottom, so the picture keeps its full vertical sharpness and only the colour is split. Sits next to *Aperture Grille*, which adds the horizontal weave on top.
- **New curvature: *Curved Aperture*.** Alongside *Curved* and *Curved CRT* there is now a third way to bend the picture: the curved tube with the stripe mask over it, and no horizontal lines at all. Like the other two it lays over whatever look you already have, so you can put tape damage or a colour process on a striped tube and it stays striped.

## 1.14.0 — 2026-08-02
- **Fill the curved screen (*Tube fill*).** Bending the picture like an old tube pulls it inwards, which is why *Curved* and *Curved CRT* always left black bands running along the top and bottom of your screen. The new *Tube fill* slider in LOOKS pushes the picture back out: at 50% its edges sit flush against the frame with nothing cropped away, at 100% even the corners reach it — the same overscan every real television did. Left at 0% the tube looks exactly as it did before.
- **New screen look: *Antenna*.** Watching over the air, the way it actually was. A signal that drifts in and out on its own: for a while the picture is clean, then it sags — the colour fades out first and the picture drops to black and white, a ghost of the image slides in beside itself, everything goes soft and starts to flicker with snow, lines tear, a bar drifts slowly up the screen. A passing aircraft makes the whole thing beat for a few seconds; a fridge or a passing car writes short bright dashes across the picture; and every so often lightning wipes a band of it. Then it settles down again. Nothing loops, nothing repeats, and the *Strength* slider decides how bad your reception is.
- **New screen look: *Antenna + VHS*.** The same reception, recorded onto tape — a home recording of a broadcast that wasn't coming in properly. The signal damage happens before the tape gets it and the tape damage sits on top, which is the order it happened in back then, and it looks it.
- **Sliders keep the value you set.** Opening a slider tile (*Strength*, *Scanlines*, any of them) could snap it to a completely different value the moment your hand moved — because the tile you clicked sits underneath the big slider that pops up, so the click was read as a drag. Your setting now stays exactly where you put it, and the slider only moves when you actually drag it.
- **The menu stays smooth at any frame limit.** The frame cap is meant for the video, but it was pacing the interface too — at 24 or 30 fps the menus, sliders and fades ran like a slideshow. Menus now always animate at 60 fps, whatever the video is capped to.
- **"Are you still watching?"** Fall asleep mid-film and the player notices. After the time you pick (30–120 min) without a single key, click or remote press, it pauses so you miss nothing and asks. A card asks on screen, with a countdown of what happens if nobody answers — after five minutes it does what you told it to: stay paused, quit, send the PC to sleep, or shut it down. Any key, click or remote press answers it and plays on. Off by default; both settings live in APP.
- **Frame cap tiles are full size.** The frame-limit page had nineteen options, one row more than the honeycomb holds, so all its tiles shrank. Two limits nobody's display actually runs (200 and 280) are gone and the page now matches every other menu.

## 1.13.2 — 2026-07-28
- **Surround, without the echo.** *Surround* was mixing in a delayed copy of the opposite channel on every track — a full-range echo that hollowed out voices and anything sitting in the middle of the mix, and made music sound like it was coming through a pipe. It's gone. The stage is now widened where widening belongs (the treble) and tightened where headphones exaggerate it (the bass), and centred sound — dialogue, most vocals, anything mono — now passes through completely untouched.
- **Loudness that doesn't cost you quality.** The automatic level control used to push every single sample through a distortion curve, whether it needed it or not. That is exactly why loud, modern-mastered music — AMVs, music videos, anything squeezed for volume — sounded *worse* with *Loudness* on than with it off. It now leaves everything below the ceiling completely alone and only catches the peaks that would really clip. On typical music that is sixteen times less distortion; on quieter material, none at all.
- **No more crackle when the volume rides.** The automatic level used to change in steps, once per audio buffer, which added a faint grain whenever it was working. It now glides smoothly, and it behaves identically on every sound card instead of changing character with the device's buffer size.

## 1.13.1 — 2026-07-26
- **Smooth curved edges.** The curved tube's outline (*Curved* and *Curved CRT*) rendered as hard pixel stairs — it's now one clean, softly-feathered line.
- **Scanlines slider, scanlines only.** Turning the *Scanlines* strength down no longer strips the CRT's colour mask (and the ring pattern it draws on the tube) with it — the slider now dims just the horizontal lines. A completely bare tube is still one tap away: that's the *Curved* toggle.
- **Network dot fixes.** The little online indicator in the menu sat exactly in the window's close button — moved below the title bar. And it now turns green while a network stream is playing, not only when your lights are being driven.

## 1.13.0 — 2026-07-26
- **Place your lights around the screen (Light layout).** New *Layout* button in the LIGHTS menu opens a top-down view: your screen sits in the middle and each lighting output (WLED, OpenRGB, sACN, Chroma, Hue, Home) is a chip you drag to where it physically sits — above, left, a corner, wherever. Each one then glows the colour of *that* side of the picture instead of a single average, so the light around your room actually follows the scene directionally. Leave a device on the screen to keep the whole-frame average as before.
- **Every RGB device, placed individually.** Tap the *OpenRGB* chip in the layout and every device OpenRGB knows — Corsair, ASUS, Razer, MSI, keyboard, RAM, fans, GPU — appears as its own chip to place around the screen, several per side if that's how your desk looks. Devices you plug in later show up on their own (no reconnect needed), and a bug that made RGB *keyboards* silently stay dark is fixed. Tap *Chroma* for the same per-device placement of Razer Synapse gear.
- **Profiles.** Save your entire current setup under a name you type — one for anime, one for retro nights, one for the kids — and switch with one tap (APP → *Profiles*). Loading a profile never touches machine things like your Hue pairing or device addresses.
- **Your remote controls and media keys work now.** Play/Pause, Next/Prev, volume and mute on media keyboards, Bluetooth remotes and headsets finally do something. Also new: **0–9** jumps to 0–90% of the video, **Shift+←/→** steps a single frame, **Shift+N** goes to the previous video, and auto-resume now *says* it resumed — press 0 to start over.
- **Phone remote in the menu.** OUTPUT → *Remote*: switch on the built-in web remote and open the shown address on your phone (same Wi-Fi) — play/pause, seek and volume from the couch. No more hidden environment variable.
- **SponsorBlock.** New toggle in the stream settings: sponsor and self-promo segments in supported streams are skipped automatically, with a small note telling you how much you didn't have to sit through.
- **Sideways phone videos play upright.** Videos recorded in portrait (or with rotation metadata) are now rotated automatically — pixel-exact, on the GPU.
- **Chapter list.** MEDIA → *Chapters*: the seek-bar tick marks as a named, tappable list — jump straight to a chapter instead of blind-stepping through them.
- **Sound fixes.** Loud, wide music (AMVs) distorted badly with *Surround* on — fixed with a proper limiter. Some sound drivers got permanent silence — fixed. And switching Windows' default output (plugging in a USB DAC, connecting Bluetooth) now moves the sound over immediately instead of staying on the old device.
- **A corrupt spot in a file no longer ends playback.** The decoder now skips damaged packets and carries on at the next clean frame instead of stopping as if the video were over.
- **Sleep timer.** APP → *Sleep timer* (30/60/90/120 min): FAFI quits cleanly when the time is up — doze off without it playing all night.
- **Screenshots are clean PNGs now.** F9 saves a PNG of just the picture (your filters and retro look included) — no more seek bar or menus baked into a bulky BMP.
- **Stats view.** Press **F** twice for a full stats card: resolution, decode path, real video/render rates, audio format and glitch counter, A/V offset — for when you want to know exactly what the player is doing.
- **Network permission.** The first time a lighting output or Home Assistant wants your network, FAFI asks first — allow or block, once or permanently. A subtle dot in the menu (top right) shows green while FAFI is actually talking to your network, red when it isn't.
- **Menu polish.** Every tile now has a hover explanation (including the LOOKS page and all AMBIENT sliders — and *Dyn peak* finally explains itself), tiles are the same size on every page, the keyboard-help page lists all the real shortcuts and is translated, and the streaming *Stream login* picker (which browser's login to use for members-only streams) is in the menu too.
- **Crash reports.** If FAFI ever crashes, it now writes a small `crash_….dmp` file (in `%LOCALAPPDATA%\FAFI`) you can attach to a bug report — crashes stopped being invisible.
- **Under the hood.** Settings lines longer than 160 characters no longer get corrupted; chapter titles, stream quality and more survive reloads properly.

## 1.12.0 — 2026-07-24
- **The FPS readout holds steady now.** With a frame-rate cap set (e.g. 165), the counter used to lurch wildly — 150 one moment, 800 the next — especially on G-Sync / FreeSync screens. The cap is now enforced by a steady software limiter instead of a self-correcting guess that fought itself, so the number sits where it should (at or below your cap) and stops jumping around.
- **Smoother RIFE playback.** Neural interpolation (RIFE) now runs on its own worker thread instead of blocking each frame, so the picture presents smoothly and the menu/seek stay responsive while it works — no more hitching at the network's pace on slower GPUs. The interpolation itself is unchanged; it just no longer stalls everything else.
- **Razer Chroma lighting.** New *Chroma* toggle in the LIGHTS menu: your Razer keyboard, mouse, mousepad, headset and other Chroma gear now glow in the colour of what's on screen, via Razer Synapse — alongside the existing WLED, OpenRGB and sACN outputs.
- **Philips Hue lighting.** New *Hue* toggle: your Hue room lights follow the colour of the picture. First time, press the link button on your Hue bridge once when prompted — after that it just works. The bridge is found on your network automatically.
- **Home Assistant / MQTT (two-way).** New *Home* toggle: FAFI publishes the on-screen colour to your MQTT broker and announces itself to Home Assistant automatically as a light called *FAFI Ambient* — mirror it onto any smart bulbs with an automation. It also adds **control buttons** (Play/Pause, Next, Previous, Mute, Fullscreen) to Home Assistant, so an automation or dashboard can drive FAFI back. Set your broker address (`mqtthost`) in the settings file.

## 1.11.1 — 2026-07-24
- **Chapters.** Files that carry chapters (most MKV/MP4) now show small tick marks on the seek bar, and **Ctrl + ← / →** jumps to the previous / next chapter — with the chapter number and title flashed on screen. Works like a disc player: a quick "previous" restarts the current chapter unless you're right at its start.
- **Match display to the video (Match Hz).** New *Match Hz* toggle (Output menu): when on, FAFI switches your monitor to a multiple of the video's frame rate — e.g. a 23.976 fps film on a 165 Hz screen drops it to 144 Hz — so 24p plays with dead-even pacing instead of the classic 3:2 judder that interpolation otherwise has to hide. Off by default; your original refresh rate is always restored when the video changes or the player closes (even on a crash).
- **No more freeze when quitting mid-load.** Closing the player while a video was still opening could very occasionally leave the window stuck and only killable from Task Manager — fixed. Exit is also cleaner under the hood (no stray crash logged after close), and the build now only loads its libraries from trusted locations.
- **See what's playing, and time remaining.** The title bar now shows the file name (or the stream's title) instead of just the app name. And clicking the time on the seek bar flips it between *elapsed / total* and *−remaining / total* — your choice is remembered.
- **The honeycomb menu is fully translated now.** The category headers (Media, Picture, Output, Lights, …) were still showing in English in other languages — they now match the language you picked, like the rest of the menu.

## 1.11.0 — 2026-07-23
- **Hover help in the menu.** Rest the pointer on any setting tile for a second and a little card pops up beside it explaining what the setting does — in your language.
- **Seek previews you can actually read.** The thumbnail preview now stays up the whole time you drag the seek bar (even when your cursor drifts off it), and it's bigger and sharper — readable from the couch.
- **Frame-rate cap now sticks.** Setting a cap (e.g. 165) is now enforced even on G-Sync / FreeSync screens, where it used to be ignored.
- **HDR passthrough & dynamic tone mapping in the menu.** Both can now be toggled from the honeycomb menu instead of only via a startup switch.
- **AI upscale for real footage too.** Export AI-upscaling now also handles live-action video, not just anime — drop the model in and pick it.
- **Calmer menu.** The BACK tile's arrow no longer wiggles.

## 1.10.2
- **Finer VHS tape dropouts.** The bright streaks in the *VHS PAL* look are now hairline flickers instead of thick white bars — subtle wear, not a damaged tape.

## 1.10.1
- The **Aspect ratio** control is now in the honeycomb menu too (under *Picture*), not just the classic menu.
- Menu tile text now **scales with the tiles** — labels stay neatly sized when the window is small.

## 1.10.0
- **The player now speaks your language.** A new language picker with **12 languages** — English, German, French, Spanish, Italian, Portuguese, Dutch, Polish, Russian, Turkish, Japanese and Chinese. Switch any time; your choice is remembered.
- **Open and view images.** Drop a PNG, JPG, WebP, BMP or TIFF onto the player and it shows the picture — with the same zoom and aspect controls as video.
- **Correct aspect ratio, automatically.** Videos that used to look stretched now display at their true shape, and a new **Aspect ratio** option lets you choose fit, crop-to-fill, or stretch.

## 1.9.5
- Cleaner names for the retro screen looks so it's obvious what each one does at a glance.

## 1.9.4
- **Ambient light gets a soft, borderless edge.** A new *Border* slider lets the picture melt into its own glow instead of ending on a hard rectangle, with gently rounded corners.

## 1.9.3
- **Curved-CRT scanlines are now adjustable** — dial the "magnetic lines" from a clean curved tube all the way up to a full old-school CRT.

## 1.9.0
- **Ambient light, refined:** smoother, seamless glow with clearer labels.
- **VHS look** gained authentic tape dropouts for extra nostalgia.
- Subtitles now stay correctly inside the picture even with curved screens, retro filters, or a shrunk image.

## 1.8.x
- **Update without reinstalling.** FAFI can now update itself in place with a single click — verified for authenticity before it installs.
- **Jump anywhere instantly**, even in long streams, with smart range-based seeking.
- **Kaleidoscope** and a fully in-player **Ambient Light** suite: choose which sides glow, tune blur, spread, brightness and colour, and it works alongside every filter and the curved screen.
- Big, comfortable sliders for fine-tuning, and a tidier, better-grouped menu.

## 1.7.0
- **Accessibility suite (Meatware Mods):** colour-blind correction, dialogue boost, mono downmix, a photosensitive flash guard, a calmer low-motion UI, and slow-playback that can auto-engage while subtitles are on screen.
- **Recently played** history so you can pick up where you left off.
- Adjustable subtitle position, a more reliable always-on-top, and broader hardware decoding support.

## 1.6.x
- **Ten creative screen looks** — CRT, aperture grille, LCD, VHS, NTSC, 35mm film, digital glitch, old handheld, e-paper, and more — plus a clean anime mode.
- **HDR tone mapping** for HDR10/HLG sources, so highlights no longer wash out on SDR screens.
- **Smarter upscaling** that picks the best method for your GPU and content, with an anime line-art mode.
- The RIFE model is now built in — smooth interpolation works out of the box, offline.
- Backup and restore all your settings from a single file, and a manual "check for updates".
- A polished glass menu with a crisp, embedded typeface.

## 1.5.x
- **Full subtitle package:** load your own subtitles, auto-fetch them for online sources, style them your way, and export them (as a track or burned in).
- **Before/after wipe** to see FAFI's effect live, side by side.
- **Export** your interpolated and upscaled video, single files or in batch, with optional neural upscaling.
- More robust playback for online sources and long videos, and the player can always be closed cleanly.

## 1.2 – 1.5
- **Play almost anything:** a wide range of file formats and online sources.
- **Play while it downloads** for a fast, smooth start.
- Repeat modes, a distraction-free fade-out of the controls, and a clean single-window experience.

## 1.0 – 1.1
- The first public FAFI: **real-time frame interpolation** for buttery-smooth motion, with a modern, GPU-accelerated player.
- Picture controls (brightness, contrast, saturation, sharpness, warmth), volume and audio options, fullscreen, and picture-in-picture.

---

*Questions or ideas? You're always welcome to reach out — FAFI keeps getting better because of feedback like yours.*
