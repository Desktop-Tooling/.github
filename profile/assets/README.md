# Desktop Tooling brand assets

Maintainer index. The org profile at `profile/README.md` renders `./assets/logo-mark.svg`.

## Live files

| File | Role |
| --- | --- |
| `logo.svg` | Isolated glyph, transparent, no app tile — site and docs header |
| `logo-icon.svg` | Same glyph; the documented small-logo / favicon source |
| `favicon.svg` | Same glyph; SVG favicon |
| `logo-glyph-mono.svg` | Single `evenodd` path, `fill="currentColor"` — badges and inline UI |
| `logo-mark.svg` | Glyph on the steel app tile — profile README, avatar, app icons |
| `logo-mark.png` | 500 px raster of the mark |
| `logo-mark-256.png` | 256 px raster of the mark; upload this as the GitHub org avatar |
| `favicon.ico` | Multi-size ICO (256…16) rendered from the glyph on a square canvas |

## Revisions

Every revision is harboured under `brand/<revision>/` with a `SOURCE.txt`.

| Revision | Note |
| --- | --- |
| `brand/2026-09-07-explorer-socket/` | Current. Two-pane desktop window with a hex-drive socket. |

The retired 2026-08-19 monitor-and-driver mark is recoverable from git history.

## Regenerate rasters

Run from the repo root with ImageMagick 7 on PATH.

```powershell
$b = "profile/assets/brand/2026-09-07-explorer-socket"
$a = "profile/assets"

magick -background none -density 600 "$b/desktop-tooling-mark.svg" -resize 500x500 "$a/logo-mark.png"
magick -background none -density 600 "$b/desktop-tooling-mark.svg" -resize 256x256 "$a/logo-mark-256.png"

# ICO frames must be square, so pad the landscape glyph before converting.
magick -background none -density 600 "$b/desktop-tooling-glyph.svg" `
  -resize 240x240 -gravity center -extent 256x256 "$env:TEMP/dt-glyph-256.png"
magick "$env:TEMP/dt-glyph-256.png" -define icon:auto-resize=256,128,64,48,32,16 "$a/favicon.ico"
```

Copy the SVGs unchanged into the sibling repos — do not fork diverging masters:

- `Desktop-Tooling.github.io/public/logo.svg`, `logo-mark.svg`, `logo-mark-256.png`, `apple-touch-icon.png`
- `docs/docs/modules/ROOT/images/logo.svg`, `docs/supplemental-ui/img/logo.svg`

## Palette

| Token | Hex | Use |
| --- | --- | --- |
| amber | `#E8A838` | the glyph, every stroke and fill |
| steel | `#101820` | app tile ground (mark only) |
| slate | `#243140` | thin tile rim (mark only) |
| glass | `#7EC8E3` | brand accent for UI; deliberately absent from the mark |
