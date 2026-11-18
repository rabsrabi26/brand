# rabsrabi brand

The shared identity for [rabsrabi.com](https://rabsrabi.com), **rabsrabi / notes** ([blog.rabsrabi.com](https://blog.rabsrabi.com)) and the **rabsrabi / admin** panel ([auth.rabsrabi.com](https://auth.rabsrabi.com)).

The guide is a static page, served from this repository with GitHub Pages at [brand.rabsrabi.com](https://brand.rabsrabi.com). It uses the kit it documents.

## The idea: Signal & Ink

- **Ink** is the writing: navy-tinted neutrals and quiet type.
- **Signal** is the network: one teal that marks what you can act on.
- Labels, dates and figures use a mono face with real units.

## What is in here

| Path | What it is |
|---|---|
| `index.html` | The brand guide: logo, color, type, components, rollout |
| `v1/brand.css` | Design tokens (light and dark) and shared components |
| `v1/tokens.css` | The tokens alone, for a site that keeps its own component CSS |
| `v1/brand.js` | Theme switch, logo symbols and the command palette |
| `v1/logo/` | Logo mark as SVG: light, dark and the small-size version |
| `v1/favicon.svg`, `v1/*.png` | Favicon, Apple touch icon and 192 / 512 px app icons |

`v1` stays backward compatible: it only gains features (1.1.0 added `tokens.css`, the `themechange` event and the palette opt-out). Breaking changes go in `v2`, so a site never changes under its own feet.

## Use it in a site

Add this to the `<head>`:

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Bricolage+Grotesque:wght@500;600;700;800&family=Instrument+Sans:wght@400;500;600;700&family=JetBrains+Mono:wght@400;500;600&display=swap">
<link rel="stylesheet" href="https://brand.rabsrabi.com/v1/brand.css">
<script src="https://brand.rabsrabi.com/v1/brand.js"></script>
```

- **Logo:** inside an element with class `lockup`, add `<svg class="mark"><use href="#rs-mark"/></svg>` and then `<span class="wm">rabs<i>rabi</i></span>`. Notes and admin add `<span class="sub">/ notes</span>` or `<span class="sub">/ admin</span>`.
- **Theme:** any buttons with `data-theme-choice="auto"`, `"light"` or `"dark"` work. The choice is saved in a cookie on `.rabsrabi.com`, so it carries across all three sites.
- **Command palette:** `Ctrl/Cmd + K` or `/` opens it. Add a site's own entries with `RabsBrand.palette.setItems([{ group, label, hint, href }])`. Links to the three sites and the theme choices are built in. Any element with `data-palette-open` opens it on click.

A site with its own command palette sets `window.RABS_BRAND = { palette: false }` before loading `brand.js`. The page then receives a `themechange` event whenever the theme changes, so canvases and charts can redraw.

Use the tokens in your own CSS, for example `color: var(--muted)` or `background: var(--surface)`, and never hard-code a hex value. Every color has a light and a dark value.

## DNS and Pages

1. In this repository, open **Settings → Pages**, choose **Deploy from a branch**, then `main` and `/ (root)`.
2. At your DNS provider, add a `CNAME` record: host `brand`, target `rabsrabi26.github.io`.
3. When it is available, turn on **Enforce HTTPS**.

The `CNAME` file in this repository already names `brand.rabsrabi.com`.

## Rules in one place

- Text meets WCAG AA (4.5 : 1) in both themes. Control borders meet 3 : 1.
- Logo below 28 px uses the small mark. Never recolor the arcs.
- One accent per screen area. Signal appears once or twice per view.
- Touch targets are at least 44 px. Focus is a 2 px Signal ring, always visible.

Full detail, with live examples, is in the guide.
