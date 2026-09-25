# Desentral Projects & Civil Works — Website

Student web design project — Part 2: CSS styling and responsive design.

A 5-page static HTML/CSS/JS website for Desentral Projects & Civil Works, a
Johannesburg-based construction and renovation company (est. 2015). No build
tools, frameworks, or server required — open `index.html` in any browser and
the whole site works.


## Folder structure

```
root/
|
|-- index.html              Home -- carousel, slideshow strip, services, CTA
|-- about.html               About -- company story, why-choose-us
|-- projects.html             Projects -- full photo gallery (58 photos), tagged by trade
|-- admin.html                  Gallery Admin -- owner-only mockup, not linked from public nav
|-- quote.html                    Get a Quote -- form that opens WhatsApp
|
|-- css/
|   `-- style.css            Single external stylesheet for the whole site
|
|-- js/
|   `-- script.js            Nav toggle, carousel, quote form -> WhatsApp
|
|-- images/                   All project photos (Facebook exports + originals)
|   `-- responsive/            Resized 480w/800w/1200w variants for srcset
|
|-- screenshots/               Desktop/tablet/mobile evidence for this README
|
|-- sitemap/
|   `-- sitemap.JPG             Site structure diagram
|
|-- wireframes/                 Low-fidelity layout mockups (PowerPoint, Part 1)
|
`-- README.md                   This file
```


## What Part 2 added

Part 1 delivered pure semantic HTML with no styling at all — no `<link>`,
no `<script>`, no inline styles. Part 2 builds the external stylesheet and
JavaScript on top of that structure, and makes the site responsive.

**`css/style.css`** — one shared stylesheet, linked from all five pages.
Organised into: a light CSS reset, custom-property design tokens (colour,
type scale, spacing), base typography, layout primitives, then
component-by-component styling (header, carousel, cards, forms, footer),
finishing with the media queries.

- **Layout**: CSS Grid for the card grids (`grid-template-columns`) and for
  the header (`grid-template-areas: "logo nav toggle actions"`), Flexbox for
  the nav list, button rows, and form rows — Grid where the layout is
  two-dimensional, Flexbox where it's a single row/column.
- **Typography**: a `rem`-based type scale (`--step--1` through `--step-5`)
  set as custom properties, so every heading and body size traces back to
  one scale instead of one-off pixel values.
- **Visual styling**: colour, `border`, `box-shadow` on cards and buttons,
  plus `:hover`/`:focus-visible`/`:active` states throughout (nav links,
  buttons, form fields, gallery thumbnails).
- **Responsive design**: three breakpoints — desktop (default, ≥1024px),
  tablet (≤1024px), mobile (≤640px) — implemented with `max-width` media
  queries. Multi-column grids collapse to two columns on tablet and one on
  mobile; the header nav becomes a toggled dropdown below 640px.
- **Relative units**: `rem` for font sizes and most spacing, `em` for
  spacing that should scale with local font-size (e.g. section padding),
  `%`/`vw` for the carousel and image widths.
- **Responsive images**: `srcset` + `sizes` on the 5 carousel photos, the
  4 slideshow thumbnails, and the About page hero photo — each ships
  480w/800w (and 1200w for the largest) resized JPEGs alongside the
  original, so the browser picks the smallest file that still looks sharp
  at its rendered size. The full 58-photo Projects gallery uses
  `loading="lazy"` instead, given the number of images involved (see
  "Known limitations" below).

**`js/script.js`** — mobile nav toggle, the home page carousel (autoplay,
manual prev/next, dot navigation), and the quote form, which builds a
WhatsApp message from the filled-in fields and opens `wa.me` with it
pre-filled. No backend involved anywhere on the site.


## Screenshot evidence — desktop / tablet / mobile

Rendered directly from the finished HTML/CSS at three viewport widths:
**desktop 1440px**, **tablet 768px**, **mobile 375px**.

### Home

| Desktop | Tablet | Mobile |
|---|---|---|
| ![Home desktop](/Website/screenshots/index-desktop.png) | ![Home tablet](/Website/screenshots/index-tablet.png) | ![Home mobile](/Website/screenshots/index-mobile.png) |

Mobile nav menu, open:

![Home mobile nav open](/Website/screenshots/index-mobile-nav-open.png)

### About

| Desktop | Tablet | Mobile |
|---|---|---|
| ![About desktop](/Website/screenshots/about-desktop.png) | ![About tablet](/Website/screenshots/about-tablet.png) | ![About mobile](/Website/screenshots/about-mobile.png) |

### Projects

| Desktop | Tablet | Mobile |
|---|---|---|
| ![Projects desktop](/Website/screenshots/projects-desktop.png) | ![Projects tablet](/Website/screenshots/projects-tablet.png) | ![Projects mobile](/Website/screenshots/projects-mobile.png) |

### Get a Quote

| Desktop | Tablet | Mobile |
|---|---|---|
| ![Quote desktop](/Website/screenshots/quote-desktop.png) | ![Quote tablet](/Website/screenshots/quote-tablet.png) | ![Quote mobile](/Website/screenshots/quote-mobile.png) |

### Gallery Admin

| Desktop | Tablet | Mobile |
|---|---|---|
| ![Admin desktop](/Website/screenshots/admin-desktop.png) | ![Admin tablet](/Website/screenshots/admin-tablet.png) | ![Admin mobile](/Website/screenshots/admin-mobile.png) |


## Changelog

> **Note:** The entries below cover the Part 2 CSS/responsive work.
> This document should also list the specific corrections made in response
> to the Part 1 marker's feedback — add those as dated entries under
> "Part 1 feedback corrections" once you have your mark sheet, so the
> lecturer can see exactly what changed and why.

### Part 1 feedback corrections
- add entries here once Part 1 feedback is received — one bullet per
  correction, e.g. "Fixed heading hierarchy on about.html: h3 was used
  before h2" or "Added missing alt text on gallery images"

- add git hub pushed all files to git up with commit  

### Part 2 — CSS styling and responsive design
- Added `css/style.css`, linked from all five pages: reset, custom-property
  design tokens, typography scale, layout, component styling.
- Added `js/script.js`, linked from all five pages: nav toggle, home page
  carousel, quote form → WhatsApp handoff.
- Implemented responsive design with three breakpoints (desktop, tablet
  ≤1024px, mobile ≤640px); multi-column grids collapse appropriately at
  each breakpoint and the nav becomes a toggled mobile menu.
- Added `srcset`/`sizes` responsive images for the carousel, slideshow
  thumbnails, and About hero photo, with resized 480w/800w/1200w variants
  generated into `images/responsive/`.
- Added `loading="lazy"` to all 58 Projects gallery images.
- Fixed a contrast bug found during testing: the "See our work" outline
  button was rendering dark-on-dark over the carousel photo.
- Fixed missing vertical spacing between headings and the elements that
  follow them (a side effect of the CSS reset zeroing all margins by
  default) — added a default `margin-bottom` to `h2`/`h3` in the base
  typography rules.
- Hid the per-slide caption badge on tablet widths, where it was
  overlapping the carousel's call-to-action buttons.
- Captured desktop/tablet/mobile screenshots of all five pages as evidence
  (see "Screenshot evidence" above).


## References

Referenced per **The IIE's Harvard-Anglia style guide** (2026 edition).

Desentral Projects & Civil Works, [s.a.]. *Desentral Projects & Civil
Works*. [Facebook] Available at: <https://www.facebook.com/Decentral>
[Accessed 20 August 2026].

*(All project photos in `images/` were supplied by the site owner and
sourced from the company's own Facebook page, referenced above.)*


## Known limitations / next steps

- **Admin page**: `admin.html` is a front-end mockup only — the "Add to
  gallery" form does not submit anywhere or touch the file system. Adding
  a new photo currently means manually saving the file into `images/` and
  adding a matching `project-card` entry in `projects.html`. A real
  owner-login-and-upload flow would need a backend (Firebase Auth +
  Storage, or PHP/MySQL) — not implemented in this static build.
- **Responsive images**: `srcset`/`sizes` is implemented for the featured
  carousel, thumbnail strip, and About hero photo (10 unique files). The
  58-photo Projects gallery uses `loading="lazy"` for performance instead
  of full srcset, given the number of images involved — extending srcset
  across the whole gallery would be the natural next step.
- **Testimonials**: no client testimonial content has been supplied yet.


## Contact (as shown on the site)

| | |
|---|---|
| Phone / WhatsApp | 064 094 8066 |
| Email | desentralprojects@gmail.com |
| Facebook | facebook.com/Decentral |
| Coverage area | Johannesburg & greater Ekurhuleni, South Africa |
