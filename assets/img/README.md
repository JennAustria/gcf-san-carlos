# Church images & logo — drop your real files here

The site is wired to **auto-detect** these files. Add a file with the exact name below
and it appears on the site automatically — no code changes needed. Until a file exists,
a branded gradient placeholder is shown, so the site never looks broken.

> Tip: keep images optimized (JPG/WebP, ~1600px wide max, < 300 KB each) for fast loading.

## Auto-wired (just add the file with this exact name)

| File | Where it appears | Recommended size |
|------|------------------|------------------|
| `logo.svg` (or `logo.png` / `logo.webp`) | Navbar + footer (replaces the "G" monogram) | square or wide, transparent bg, ~88px tall |
| `hero.jpg` | Home hero background (subtle overlay) | 2000 × 1200, dark/worship scene works best |
| `about.jpg` | "Who We Are" image on Home **and** About pages | 1000 × 1250 (portrait) |
| `give.jpg` | "Your Impact" image on the Give page | 1000 × 1250 (portrait) |
| `leaders/daniel.jpg` | About → leadership headshot #1 | 600 × 600 (square) |
| `leaders/maria.jpg` | About → leadership headshot #2 | 600 × 600 (square) |
| `leaders/joseph.jpg` | About → leadership headshot #3 | 600 × 600 (square) |
| `og.jpg` | Social-share preview (Facebook/Twitter) | 1200 × 630 |
| `favicon.png` | Browser tab icon — see note below | 512 × 512 |

> Rename the leadership files (or tell me your real pastors' names) and I'll relabel them.

## CMS images (set the path inside the JSON files)

For sermons, events, and ministries, save your photo here and point to it in the matching
`assets/data/*.json` file. Example for a sermon thumbnail:

```json
"thumbnail": "assets/img/sermons/rooted.jpg"
```

Suggested subfolders (create as needed):
- `assets/img/sermons/` — sermon thumbnails (1280 × 720)
- `assets/img/events/`   — event cover images (1280 × 720)
- `assets/img/ministries/` — ministry photos (1000 × 1000 or 1280 × 720)

## Page images you can also replace

These currently use placeholders. To use a real photo, tell me the filename and I'll wire
it, or replace the placeholder block on the page:
- About page: church/community photo, plus leadership headshots
- Give page: a generosity/outreach photo
- Home "About" section: a church-family photo

## Favicon (optional)
Add `favicon.png` here, then add this line inside each page's `<head>`:
```html
<link rel="icon" href="assets/img/favicon.png" />
```
(I can add this across all pages for you on request.)
