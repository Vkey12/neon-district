# NEON DISTRICT // Sector 7

A single-file, cyberpunk-themed interactive webpage. Dark neon aesthetic, animated
synthwave scene, glitch typography, and a fully working fake terminal.

**File:** `neon-district.html` (self-contained — HTML, CSS, and JS in one file)

---

## Quick Start

No install, no build step, no server required.

1. Double-click `neon-district.html`, **or**
2. Open it with your browser:

```bash
# Linux
xdg-open ~/Desktop/neon-district.html

# macOS
open ~/Desktop/neon-district.html

# Windows
start %USERPROFILE%\Desktop\neon-district.html
```

Works in any modern browser (Chrome, Firefox, Edge, Safari).

---

## What's On The Page

### Animated background
A canvas-rendered synthwave scene behind all content:

- Retro neon sun with horizontal slit bands
- Infinite perspective grid scrolling toward the viewer
- Twinkling starfield and drifting acid-rain streaks
- Racing traffic lights along the horizon
- CRT scanlines, flicker, and vignette overlays

### Boot sequence
On load, a fake `NIGHT-OS` BIOS boots up with typed log lines and a progress bar.
Click anywhere to skip it.

### Interactive terminal
Type commands into the shell at `root@nd:~#`:

| Command   | What it does                                                        |
|-----------|---------------------------------------------------------------------|
| `help`    | Lists all available commands                                        |
| `scan`    | Scans nearby network nodes and reports latency                      |
| `hack`    | Runs a full animated breach sequence with progress bars             |
| `signal`  | Generates a new cyberpunk signal codename                           |
| `whoami`  | Shows your visitor session ID and clearance level                   |
| `matrix`  | Take the red pill                                                   |
| `coffee`  | Requests the caffeine module (spoiler: it's offline)                |
| `clear`   | Wipes the terminal output                                           |
| `about`   | Explains what the page is                                           |

### Buttons

- **Initiate Hack** — runs the full hack sequence, updates the signal readout,
  randomizes the system meters, and shakes the screen. Also bound to the `H` key
  anywhere on the page.
- **Randomize Signal** — generates a fresh codename, updates the threat meter,
  and re-rolls the status bars.

### Other details

- Live HUD clock (local system time)
- Auto-scrolling news ticker
- Neon stat counters that animate on load
- Three "modules" cards with cursor-tracking glow on hover
- A custom crosshair cursor that expands over interactive elements
- Subtle WebAudio blips on clicks and commands (only after a user gesture)

---

## Customization Cheatsheet

Everything lives in the one file. Open it in a text editor.

### Colors
Find the `:root` block near the top of the `<style>` section:

```css
:root{
  --bg:#05010d;        /* page background            */
  --cyan:#00f5ff;      /* primary neon accent        */
  --magenta:#ff2bd6;   /* secondary neon accent      */
  --yellow:#f9f002;    /* highlight / warning        */
  --ink:#d9fbff;       /* main body text             */
}
```

Change these and the whole page re-themes.

### Title and copy
Search the HTML for these strings:

- `NEON DISTRICT` — the big glitch heading (update `data-text` too, or the
  glitch layers will show the old text)
- `A rogue signal is bleeding out...` — hero paragraph

### Terminal commands
Find the `commands` object inside the `<script>` block:

```js
const commands = {
  help(){ ... },
  scan(){ ... },
  ...
};
```

Add your own the same way — each value is a function that calls
`print('your text', 'ok')`. Available classes: `dim`, `ok`, `warn`, `err`,
`hi`, `cyan`, `user`.

### Signal codenames
Edit the `ADJ` and `NOUN` arrays to change the generated names
(`CHROME_RONIN-9F3A` style).

### Ticker headlines
Search for `<div class="ticker-track"` and edit the `<span>` items. Keep the
list duplicated (the animation scrolls to `-50%` for a seamless loop).

### Disable animations
The page already respects the OS-level "reduce motion" setting. You can also
delete the `@media (prefers-reduced-motion: reduce)` block to always animate,
or remove the canvas scene by deleting `<canvas id="bg">`.

---

## Tech Notes

- **No dependencies.** Pure HTML/CSS/JS. The only external request is Google
  Fonts (Orbitron + Share Tech Mono); if you're offline it gracefully falls
  back to system fonts.
- **No tracking, no network calls, no data collection.** Everything runs locally.
  All "hacking" is decorative — no real systems are touched.
- **Performance:** the canvas uses `requestAnimationFrame` and caps device pixel
  ratio at 2. Animation auto-pauses when the tab is hidden.
- **Single file:** you can copy it anywhere, email it, or host it on any static
  host as-is.

---

## Project Structure

```
Desktop/
├── neon-district.html   ← the whole thing
└── README.md            ← this file
```

---

© 2077 NEON DISTRICT — built in the dark, for fun.
