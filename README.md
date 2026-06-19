# Gospel of Christ Fellowship Church – San Carlos (GCF San Carlos)

A production-ready, **single-file** church website. The entire site — HTML, CSS,
JavaScript, and all content ("CMS") — lives inside **`index.html`**. It's a one-page,
fully responsive, accessible, SEO-optimized site with premium animations.

> Because everything is inlined, the site works even by **double-clicking `index.html`**
> (no server or build step needed). The only external pieces are Google Fonts, the Google
> Maps embed, and your church photo/logo — see below.

---

## View it

- **Easiest:** double-click `index.html`.
- **Recommended (matches hosting):** serve the folder, then open the URL:
  ```bash
  python -m http.server 8080   # then open http://localhost:8080
  ```

## Deploy

Drag the whole folder onto **Netlify** (app.netlify.com/drop), or push to Vercel /
Cloudflare Pages / GitHub Pages. No build command, output is the folder root.
The contact form already has **Netlify Forms** attributes, so submissions are captured
automatically when hosted on Netlify.

---

## Files

```
index.html            # The ENTIRE website (HTML + CSS + JS + content)
assets/img/
  hero.png            # Hero / background photo
  favicon.png         # Browser-tab icon (circular church logo)
robots.txt
sitemap.xml
```

---

## Editing content (the "CMS")

All dynamic content lives in one JavaScript object near the bottom of `index.html`:
search for **`window.GCF_DATA`**. To add a sermon, event, or ministry, copy an existing
`{ ... }` block inside the matching list and edit the text. No other changes needed.

```js
window.GCF_DATA = {
  announcements: { items: [ … ] },   // top bar (highest priority item shows)
  sermons:       { items: [ … ] },   // set "featured": true on ONE sermon
  events:        { items: [ … ] },
  ministries:    { items: [ … ] }
};
```

Sermon video: set `videoUrl` to a YouTube **embed** URL
(`https://www.youtube.com/embed/VIDEO_ID`) and it plays inline; leave blank for a card.

## Editing church details

Search `index.html` for these to update them directly in the markup:
- **Address:** Barangay Tarece, San Carlos City, Pangasinan 2420
- **Phone:** 0995 103 5373 · **Email:** gospelofchrist.sc@gmail.com
- **Facebook:** https://www.facebook.com/GCFsancarlos
- Service times are in the footer; map coordinates are `15.937685, 120.362155`.
- Search `EDITME` for the online-giving link to add.

## Photos & logo

The site auto-detects images dropped into `assets/img/` (no code changes needed):
- `hero.png` — hero background (already added)
- `logo.png` / `logo.svg` — overrides the live Facebook logo with a sharper local one
- `about.jpg`, `give.jpg`, `leaders/daniel.jpg` … — section photos (placeholders show until added)

The logo currently loads live from the church's Facebook page until a local `logo.*` is added.

---

## Accessibility, SEO & motion
- One `<h1>`, semantic landmarks, skip link, visible gold focus rings, WCAG-AA contrast
- Per-page meta, Open Graph, and `Church` JSON-LD structured data
- Smooth inertia scrolling, scroll-reveal, hero parallax, button shine — all disabled
  automatically for `prefers-reduced-motion` and on touch/small screens
