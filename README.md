# CDN

A personal static asset CDN served over [jsDelivr](https://www.jsdelivr.com/), straight from this GitHub repo. Currently hosts self-hosted web fonts.

## Usage

All assets are served from:

```text
https://cdn.jsdelivr.net/gh/johannaefageras/cdn@VERSION/PATH
```

Always pin a version tag (e.g. `@v1.0.0`) rather than `@main`. Tags are immutable and cached permanently by jsDelivr; `@main` is cached for up to 12 hours and won't reflect new pushes promptly.

## Structure

```text
cdn/
└── fonts/
    └── <foundry>/
        └── <font>/
            ├── fonts/      web font files (.woff2, .woff)
            └── index.css   @font-face rules for the font
```

Each font folder ships an `index.css` containing the `@font-face` declarations. The `src` paths inside it are relative, so they resolve correctly wherever the CSS is loaded from.

## Fonts

### Mass-Driver

| Font | Stylesheet URL |
| --- | --- |
| MD Lorien | [`…/md-lorien/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-lorien/index.css) |
| MD Nichrome | [`…/md-nichrome/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-nichrome/index.css) |
| MD Primer | [`…/md-primer/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-primer/index.css) |
| MD System | [`…/md-system/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-system/index.css) |
| MD System Condensed | [`…/md-system-condensed/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-system-condensed/index.css) |
| MD System Mono | [`…/md-system-mono/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-system-mono/index.css) |
| MD System Narrow | [`…/md-system-narrow/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-system-narrow/index.css) |
| MD UI | [`…/md-ui/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-ui/index.css) |
| MD UI XL | [`…/md-ui-xl/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-ui-xl/index.css) |
| MD UI XS | [`…/md-ui-xs/index.css`](https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-ui-xs/index.css) |

Each link points to the full jsDelivr URL for that font's stylesheet (pinned to `@v1.0.0` — bump the tag when you release).

## Loading a font

Link the stylesheet for the font you want:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/gh/johannaefageras/cdn@v1.0.0/fonts/mass-driver/md-nichrome/index.css"
/>
```

Then use the family in your CSS:

```css
body {
  font-family: 'MD Nichrome', sans-serif;
}
```

## Releasing

Adding or updating assets:

1. Add the files and commit to `main`.
2. Cut a new tag: `git tag v1.1.0 && git push --tags`.
3. Update the `@version` in any consuming projects.

The first request to a freshly tagged file triggers a fetch from GitHub, so it's slightly slower once, then served from cache.

## License

Fonts are licensed individually by their respective foundries and are hosted here under those licenses. They are not redistributable beyond the terms of each license.
