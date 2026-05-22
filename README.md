# 🎂 Happy Birthday Project

A cinematic, multi-section birthday surprise experience built with pure **HTML, CSS, and JavaScript** — no frameworks, no dependencies. The project delivers a fully animated, page-by-page birthday journey complete with floating hearts, fairy lights, realistic balloons, a theatrical curtain reveal, and a scrollable memory gallery, all driven by vanilla JS and CSS keyframe animations.

---

## What This Project Does

The app renders a single HTML page divided into five visually distinct full-screen sections. Each section is hidden by default and revealed one at a time through smooth opacity and scale transitions. The visitor begins at a cinematic hero screen and clicks through a sequence: a message slider, a celebration stage where they manually trigger light effects, music, and balloons, a curtain-reveal scene with a personal letter, and finally a photo gallery of memories. Every section is visually immersive and driven entirely by client-side JavaScript — there is no backend, no build step, and no external JavaScript library.

---

## Features

**1. Cinematic Hero Screen** — The landing section displays an animated gradient title using a CSS `@keyframes shine` sweep and a glowing neon CTA button that pulses with `neonPulse`. Floating heart particles spawn continuously from the bottom of the screen and float upward using the `floatHeart` keyframe animation.

**2. Message Slider** — A glassmorphism card cycles through three sequential messages. Each step is controlled by `nextStep()`, which hides the current `.step-content`, reveals the next one with a `fadeInScale` entrance, and advances the active dot indicator. Floating hearts run independently in this section as well.

**3. Celebration Page — Step-by-Step Flow** — The `celebFlow()` function drives a four-step interactive sequence controlled by a `celebStep` counter. Step 1 brightens the background and illuminates fairy lights; Step 2 triggers audio playback via `HTMLAudioElement.play()`; Step 3 spawns realistic balloons across the screen; Step 4 transitions to the curtain reveal.

**4. Fairy Lights** — The celebration page features a decorative fairy-light string rendered as SVG. On `window.onload`, `initFairyLights()` calculates 25 evenly spaced points along an SVG `<path>` using `getPointAtLength()` and injects teardrop-shaped `<div>` bulbs at each coordinate. When the `.bright` class is applied, the bulbs light up with warm glow and a `flicker` animation.

**5. Realistic Balloon Physics** — `spawnBalloons()` injects balloon `<div>` elements at random horizontal positions. Each balloon uses `radial-gradient` for a three-dimensional sheen effect, a `::before` pseudo-element for the balloon knot, a `::after` pseudo-element for the string, and a `balloonFloat` keyframe that animates upward over 8 seconds. Balloons auto-remove after their animation completes.

**6. Curtain Reveal** — A stage built from two overlapping `.curtain-panel` elements (left and right) styled with a royal-red repeating gradient and a gold border. Adding the `.open` class to `#stage` triggers CSS `transform: translateX()` transitions with a `skewY` tilt that sweeps the curtains apart in 2.5 seconds, revealing the personal message card beneath.

**7. Personal Message Card** — A glassmorphism card with a `backdrop-filter: blur` effect displays a personal letter using the Dancing Script font. A `startSparkles()` function continuously spawns tiny sparkle particles around the card using absolute positioning and a `sparkle` keyframe animation.

**8. Memory Gallery** — A CSS Grid layout (auto-fit columns, minimum 280px) renders six memory cards. Each card stacks an image, a dark overlay, and a hover message. On hover, the card lifts with `translateY(-15px) scale(1.03)`, the image scales to 1.1×, and the message overlay fades in. In the gallery section, background balloons and random sparkles continue generating on a timer.

**9. Audio Playback** — An `<audio>` element with the `loop` attribute plays background music when the user reaches the celebration page. Playback is wrapped in `.catch()` to gracefully handle browser autoplay restrictions.

**10. Page Transition System** — `transitionTo(pageId)` removes the `.active` class from all `.page` elements and applies it to the target. The `.page` CSS rule uses `visibility: hidden`, `opacity: 0`, and `transform: scale(1.1)` as the base state, and `.page.active` transitions to full visibility with a 1.2-second cubic-bezier easing — creating a smooth cinematic entrance for each section.

---

## Tech Stack

| Technology | Role |
|---|---|
| HTML5 | Semantic page structure and all five section layouts |
| CSS3 | All animations, transitions, glassmorphism, grid layout, responsive media queries |
| Vanilla JavaScript | Page routing, particle generation, slider logic, balloon physics, fairy lights, audio control |
| Google Fonts | Dancing Script, Montserrat, Playfair Display — loaded via `<link>` in `<head>` |
| SVG | Wire path for the fairy-light string in the celebration section |

No npm, no bundler, no build process — the project opens directly in any modern browser.

---

## Project Structure

```
Happy_Birthday_Project/
└── Happy Birthday Project/
    ├── index.html      # All five page sections — hero, slider, celebration, curtain, gallery
    ├── style.css       # CSS custom properties, page transitions, animations, layout, responsive rules
    └── script.js       # Navigation, particle system, slider, celebration flow, balloons, fairy lights, sparkles
```

### Section Breakdown (`index.html`)

| Section ID | Content |
|---|---|
| `#hero-page` | Title, subtitle, "Open Your Gift" CTA button, floating heart particles |
| `#message-slider-page` | Three-step glassmorphism slider card with dot indicators |
| `#celebration-page` | Fairy lights SVG, step-by-step celebration flow (lights → music → balloons → curtain) |
| `#curtain-page` | Theatrical curtain with personal letter message card |
| `#gallery-page` | Six memory cards in a CSS Grid, "Replay The Magic" reset button |

### CSS Custom Properties (`style.css`)

| Variable | Value | Usage |
|---|---|---|
| `--accent` | `#ff2d55` | Buttons, glows, card borders, text highlights |
| `--gold` | `#d4af37` | Curtain border accents |
| `--glass` | `rgba(255,255,255,0.05)` | Card backgrounds |
| `--bg-dark` | `#0a0a0b` | Root background color |
| `--royal-red` | `#6e0000` | Curtain panel gradient base |
| `--bulb-warm` | `#ffde6b` | Fairy light bulb color when lit |

### JavaScript Functions (`script.js`)

| Function | Purpose |
|---|---|
| `transitionTo(pageId)` | Hides all `.page` sections, activates the target by ID |
| `createHeart(containerId)` | Spawns a single floating heart particle in a given container |
| `nextStep(step)` | Advances the message slider and updates dot indicators |
| `finishSlider()` | Transitions from the slider to the celebration page |
| `celebFlow()` | Drives the four-step celebration sequence (lights → music → balloons → reveal) |
| `spawnBalloons(targetContainer)` | Creates and animates realistic balloon elements at random positions |
| `startGalleryEffects()` | Starts background balloon spawning and sparkle generation on the gallery page |
| `startSparkles(targetId)` | Continuously spawns sparkle particles around the message card |
| `initFairyLights()` | Calculates SVG path points and injects teardrop bulb elements |

---

## How to Run

1. Clone the repository
   ```bash
   git clone https://github.com/tripathipawan/Happy_Birthday_Project.git
   ```

2. Navigate into the project folder
   ```bash
   cd Happy_Birthday_Project/Happy\ Birthday\ Project/
   ```

3. Open `index.html` in any modern browser — no server or build step required
   ```bash
   # macOS
   open index.html

   # Windows
   start index.html

   # Linux
   xdg-open index.html
   ```

> **Note on Audio:** The `<audio>` element references a local file path. To enable background music, update the `src` attribute in `index.html` to point to a valid `.mp3` file on your system or a hosted URL.

---

## Repository

[https://github.com/tripathipawan/Happy_Birthday_Project](https://github.com/tripathipawan/Happy_Birthday_Project)
