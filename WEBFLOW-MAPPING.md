# Webflow Mapping Guide — GCF San Carlos

This site is delivered as production code, but it is structured to mirror Webflow exactly.
If you (or your staff) ever want to rebuild it natively in Webflow, here is the 1:1 map.

---

## 1. Style system → Webflow

| In this code | In Webflow |
|---|---|
| CSS variables in `:root` (`assets/css/styles.css`) | **Site Settings → Variables** (Webflow now supports native variables). Create the same names: `royal-blue #0b1b3a`, `midnight #050814`, `gold #d4af37`, `white`, `soft-gray #e5e7eb`. |
| `--font-head` Playfair Display, `--font-body` Inter | **Project Settings → Fonts** → add Google Fonts *Playfair Display* + *Inter*. Set Body (All Pages) font to Inter; H1–H4 to Playfair. |
| Spacing tokens `--s-1…--s-9` (8pt grid) | Use Webflow's spacing presets or a style guide page; keep multiples of 8. |
| `.btn`, `.btn--gold`, `.btn--glass`, `.btn--outline` | Create a **Button** combo-class system: base `btn` + variants. |
| Fluid `clamp()` type scale | Set H1/H2 with Webflow's rem sizes + breakpoints (Webflow has no clamp UI; use breakpoint overrides). |

> Tip: Build a hidden **Style Guide** page first with every button, heading, and card so classes exist before you design pages.

## 2. Components → Webflow Symbols / Components

| Code component | Webflow equivalent |
|---|---|
| `<header class="nav">` (in every page) | **Symbol: "Navbar"** — build once, drag onto every page. Use Webflow's native **Navbar** element for the mobile hamburger + menu. |
| `<footer class="footer">` | **Symbol: "Footer"** |
| `.announce` bar | **Symbol: "Announcement Bar"** (bind text to an Announcements collection — see below) |
| `.hero` (home) / `.pagehero` (interior) | Sections; the page hero can be a Symbol with an editable heading. |
| `.card`, `.media-card`, `.value-card`, `.give-card` | Build one **Card** component, use variants/combo classes. |
| `.cta-banner` | **Symbol: "CTA Banner"** |
| Contact form | Webflow native **Form Block** (handles submissions automatically). |

## 3. CMS Collections → Webflow Collections

Recreate these collections in **Webflow CMS** with the exact fields. The JSON files in
`assets/data/` are the source-of-truth for field names and sample content.

### Sermons  (`assets/data/sermons.json`)
| Field | Webflow field type |
|---|---|
| Title | Plain text (Name) |
| Speaker | Plain text |
| Date | Date |
| Video URL | Link / Video |
| Thumbnail | Image |
| Series Tag | Plain text or Reference (Series collection) |
| Description | Rich text / Plain text |
| Featured | Switch (boolean) |

### Events  (`assets/data/events.json`)
| Field | Webflow field type |
|---|---|
| Event Title | Plain text (Name) |
| Date & Time | Date/Time |
| Location | Plain text |
| Cover Image | Image |
| Description | Rich text |
| Category | Option (Worship / Outreach / Fellowship) |
| CTA Label / CTA URL | Plain text / Link |

### Ministries  (`assets/data/ministries.json`)
| Field | Webflow field type |
|---|---|
| Ministry Name | Plain text (Name) |
| Description | Rich text |
| Image / Icon | Image |
| Leader | Plain text (optional) |
| Category | Option / Plain text |

### Announcements  (`assets/data/announcements.json`)
| Field | Webflow field type |
|---|---|
| Title | Plain text (Name) |
| Message | Plain text |
| Date | Date |
| Priority Level | Option (high / normal / low) |
| Active | Switch |

## 4. Collection Lists → where they render

| Code target (`data-cms="…"`) | Webflow Collection List page/section |
|---|---|
| `sermons-featured` | Sermons page — a Collection List filtered to *Featured = on*, limit 1 |
| `sermons-grid` | Sermons page — Collection List, grid layout, sorted by Date (newest) |
| `events-grid` | Events page — Collection List, sorted by Date (upcoming) |
| `ministries-grid` | Ministries page — Collection List grid |
| `announcement` | Announcement bar — Collection List, filtered *Active = on*, sorted by Priority, limit 1 |
| Home previews (`data-limit="3"`) | Same collections with **Limit = 3** + a "View all" link |

## 5. Interactions → Webflow Interactions (IX2)

| Code behavior | Webflow Interaction |
|---|---|
| Navbar transparent → solid on scroll | **Page scroll → While scrolling** OR a "Navbar scrolled" interaction toggling background. |
| `[data-reveal]` fade/slide up on scroll | **Scroll into view** → move (Y 26px → 0) + fade (0 → 100%). Add small delays for stagger. |
| Card hover lift + gold glow | **Hover** → move up 6px + box-shadow. |
| Gold CTA glow | Style state + hover shadow. |
| Slow drifting hero rays / background | **Loop** interaction (subtle) or keep as CSS. |
| Mobile menu slide | Built into Webflow's Navbar element. |
| `prefers-reduced-motion` | Webflow respects reduced motion if you enable "Reduced motion" variants. |

## 6. SEO → Webflow

| Code | Webflow |
|---|---|
| Per-page `<title>` + meta description | **Page Settings → SEO** (can bind to CMS fields on template pages). |
| Open Graph / Twitter tags | **Page Settings → Open Graph**. |
| JSON-LD `Church` schema (home) | **Page Settings → Custom Code → Head** (paste the same JSON-LD). |
| `sitemap.xml` / `robots.txt` | Webflow auto-generates sitemap; robots in **Site Settings → SEO**. |
| `alt` text | Set on every image asset in Webflow. |

## 7. Forms → Webflow

The contact form (`contact.html`) uses native HTML + a graceful success message.
In Webflow, use a **Form Block**: submissions appear in **Site Settings → Forms** and can
email your team. Keep the same fields: Name, Email, Message, Prayer Request.
The current code also includes Netlify Form attributes so it works instantly if you deploy
to Netlify instead of Webflow.

---

### Summary
Everything here — palette, type, components, collections, interactions, SEO — has a direct
Webflow counterpart. You can ship this code today and migrate to Webflow later without
redesigning anything.
