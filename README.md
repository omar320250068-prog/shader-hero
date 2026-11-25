# Aurora Liquid Flow — Shader Hero

A single-file WebGL2/GLSL fragment-shader hero page. The shader draws a full-viewport aurora / liquid flow field behind the hero text and reacts to the pointer.

[Live demo on GitHub Pages](https://omar320250068-prog.github.io/shader-hero/)

## What it does

- Renders one GLSL fragment shader per pixel onto a fullscreen canvas, using hash-based value noise, five octaves of fBm, and a time-warped flow field.
- Composes three aurora layers (broad glow, curtain, fine filaments) with a palette that runs from teal through violet to magenta, plus a liquid shimmer, film grain, vignette, and a gamma lift.
- Lets the pointer stir the flow: `pointermove` and `pointerdown` update a smoothed target uniform that adds a swirl with exponential falloff around the cursor. On touch-only devices the target is eased toward a fixed point on the screen.
- Uses a WebGL2 context with a WebGL fallback; if neither is available, a CSS gradient replaces the canvas.
- Keeps the render loop responsible: device pixel ratio is capped at 2, animation pauses when the tab is hidden or the window loses focus, and `prefers-reduced-motion: reduce` renders one static frame instead of looping.
- Overlays a vignette/letterbox gradient so the headline stays readable over the glow.

## Run it locally

The page has no build step and no external assets. Open `index.html` in a browser, or use the included npm script to serve the directory:

```bash
npm run serve
```

`npm run serve` runs `npx --yes serve .`.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Hero markup, styles, GLSL fragment shader, WebGL bootstrap, and render loop. |
| `package.json` | Package metadata and the `serve` script. |
| `.gitignore` | Excludes local `.opencode/` session tooling. |

GitHub Pages serves the repository root from the `main` branch.
