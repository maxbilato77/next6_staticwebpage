# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

Static landing page for **next6 — An IT Company**, deployed at [www.next6.it](https://www.next6.it) via Azure Static Web Apps. There is no build step, no JavaScript, and no package manager — the entire site is a single self-contained `index.html` with all CSS inlined.

## Development

To preview locally, open `index.html` directly in a browser:

```bash
xdg-open index.html        # Linux
open index.html            # macOS
```

No server required — the page has no dynamic dependencies or API calls.

## Deployment

Every push to `main` triggers an automatic deploy via the GitHub Actions workflow at `.github/workflows/azure-static-web-apps-salmon-meadow-0c3133603.yml`. The deploy target is Azure Static Web Apps using the secret `AZURE_STATIC_WEB_APPS_API_TOKEN_SALMON_MEADOW_0C3133603`. PR previews are also created automatically and torn down on PR close.

## Architecture

Everything lives in `index.html`. The visual layers, from bottom to top (z-index order):

| Layer | Element | z-index | Purpose |
|---|---|---|---|
| Animated dot grid | `body::before` | 0 | CSS background-image grid drifting 40px diagonally |
| Aurora blobs | `.aurora .blob` | 0 | 3 blurred radial blobs in cyan/blue/purple |
| Dark vignette | `.overlay` | 1 | `radial-gradient` fading to `#050508` at edges |
| Floating particles | `.particles .particle` | 2 | 12 tiny dots rising with `particleFloat` keyframes |
| Ambient glow | `body::after` | 3 | Centered radial glow pulsing slowly |
| Main content | `.content` | 10 | Logo + tagline, centered with flexbox |

## Design system

- **Background**: `#050508`
- **Brand gradient**: `#00d4ff` → `#2d6aff` → `#6B21F7` (135°), applied to logo text and aurora blobs
- **Font**: Inter (300, 400, 900) from Google Fonts; preconnected for performance
- **Responsive sizing**: Logo uses `clamp(5rem, 12vw, 14rem)`, tagline uses `clamp(0.85rem, 1.8vw, 1.2rem)`

## Performance constraints

Keep these in place when editing animated elements:

- `will-change: transform, opacity` on all animated elements (aurora blobs, particles, ambient glow)
- `contain: layout style paint` on `.aurora` and `.particles` to isolate compositing layers
- Animated grid uses `will-change: transform` to stay on the GPU
