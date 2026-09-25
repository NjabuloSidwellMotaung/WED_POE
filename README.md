# Desentral Projects & Civil Works — Website

Student web design project — Part 2: CSS styling and responsive design.

A 5-page static HTML/CSS website for Desentral Projects & Civil Works, a
Johannesburg-based construction and renovation company (est. 2015). Open `index.html` in any browser and the whole
site works, nav toggle and carousel included.


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
|                              (also handles the nav toggle and carousel)
|                         
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

Part 1 delivered pure  HTML with no styling at all — no `<link>`,
no `<script>`, no inline styles. Part 2 builds the external stylesheet on
top of that structure and makes the site responsive. The brief for this
part is CSS styling and responsive design,every interactive-looking piece below is done in CSS.

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

### How the interactive-looking parts work without JavaScript

- **Mobile nav toggle** — a hidden `<input type="checkbox">` paired with a
  `<label>` styled as the hamburger icon. A `.nav-toggle-input:checked ~
  .main-nav { display: block; }` rule shows the menu when the label is
  tapped. No click handler, no script.
- **Home page carousel** — the slides are layered with `position: absolute`
  and cycled by a shared `@keyframes` fade, with each slide's
  `animation-delay` staggered via `:nth-child` so they play in sequence on
  their own.
- **Get a Quote form** — the fields help a visitor gather their thoughts,
  and a "Chat on WhatsApp" button opens a `wa.me` link. Because there's no
  JavaScript, the button can't read the typed fields and forward them
  automatically — the page says so plainly rather than pretending it does.
- **Gallery Admin mockup** — the fields are marked up as plain, disabled
  inputs rather than a working `<form>`, since there's no script or backend
  behind them yet. It exists to show what the screen would look like.



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

> **Note:** Part 2 CSS/responsive work.
> This document also list the specific corrections made in response
> to the Part 1  — add those as dated entries under
> Part 1 feedback corrections

### Part 1 feedback corrections
* Did not have git hub link and commits on part 1.
 - add commits for every change 

### Part 2 — CSS styling and responsive design
- Added `css/style.css`, linked from all five pages: reset, custom-property
  design tokens, typography scale, layout, component styling.
- Built the mobile nav toggle and the home page carousel entirely in CSS
  (checkbox/label pattern and `@keyframes`).
- Implemented responsive design with three breakpoints (desktop, tablet
  ≤1024px, mobile ≤640px); multi-column grids collapse appropriately at
  each breakpoint and the nav becomes a toggled mobile menu.
- Added `srcset`/`sizes` responsive images for the carousel, slideshow
  thumbnails, and About hero photo, with resized 480w/800w/1200w variants
  generated into `images/responsive/`.
- Added `loading="lazy"` to all 58 Projects gallery images.
- Fixed missing vertical spacing between headings and the elements that
  follow them (a side effect of the CSS reset zeroing all margins by
  default) — added a default `margin-bottom` to `h2`/`h3` in the base
  typography rules.
- Hid the per-slide caption badge on tablet widths, where it was
  overlapping the carousel's call-to-action buttons.
- Captured desktop/tablet/mobile screenshots of all five pages as evidence
  (see "Screenshot evidence" above).



## References

Desentral Projects & Civil Works, [s.a.]. *Desentral Projects & Civil
Works*. [Facebook] Available at: <https://www.facebook.com/Decentral>
[Accessed 20 August 2026].

*(All project photos in `images/` were supplied by the site owner and
sourced from the company's own Facebook page, referenced above.)*

## Contact (as shown on the site)

| | |
|---|---|
| Phone / WhatsApp | 064 094 8066 |
| Email | desentralprojects@gmail.com |
| Facebook | facebook.com/Decentral |
| Coverage area | Johannesburg & greater Ekurhuleni, South Africa |
