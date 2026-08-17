# EMUN'24 Conference Website

A single-page static website for the **NUST CEME Model United Nations Conference (EME MUN)**, built with HTML, Bootstrap 4, and custom CSS. The site introduces the conference, provides event details, and directs visitors to the external registration portal
---
## Table of Contents

- [Overview](#overview)
- [Live Site Structure](#live-site-structure)
- [Project Structure](#project-structure)
- [Tech Stack](#tech-stack)
- [Getting Started](#getting-started)
- [Page Sections](#page-sections)
- [Styling Notes](#styling-notes)
- [Assets](#assets)
- [Contact Information](#contact-information)
- [Known Issues / Improvement Ideas](#known-issues--improvement-ideas)
- [Deployment](#deployment)
- [License](#license)

## Overview

This repository contains the marketing/landing page for EME MUN, hosted by NUST College of Electrical and Mechanical Engineering (CEME). The conference was scheduled for **2nd–4th May 2024**, featuring five committees: **UNSC, SPECPOL, DISEC, SSFT, and PNA**.

The site is a single HTML file (`emun.html`) styled with Bootstrap 4.5.2 and a small custom stylesheet (`styles.css`). There is no build process, backend, or JavaScript framework involved — it's plain static HTML/CSS intended to be opened directly in a browser or served from any static file host.

## Live Site Structure

The page is a single scrollable document with an anchored navigation bar linking to the following in-page sections:

| Nav Link | Section ID | Purpose |
|---|---|---|
| About | `#about` | Introduces the conference |
| Conference Details | `#conference-details` | Full invitation text, dates, and committee list |
| Registrations | `#resources` | Registration timeline and external "Register Now" link |
| FAQ | `#faq` | Placeholder for frequently asked questions |
| Contact | `#contact` | Organizing team contact details |

## Project Structure

```
EMUN_Site/
├── emun.html              # Main (and only) HTML page
├── styles.css              # Custom site styles (overlay, navbar logo, scrollbar, register button, etc.)
├── bootstrap.min.css       # Bootstrap 4.5.2 framework (vendored, minified)
├── all.min.css             # Font Awesome 5.15.4 icon font styles (vendored, minified)
├── logo.svg                 # SVG logo asset
├── EME-logo-revised.png     # CEME/EME logo used in the navbar
├── EMUN'24.png               # Image used in the "About" section
├── emephoto.jpg              # Background image for the hero/jumbotron banner
└── README.md                 # This file
```

There is no `package.json`, build tooling, or dependency manager — all third-party libraries are vendored directly as static files.

## Tech Stack

- **HTML5** — single static page (`emun.html`)
- **[Bootstrap 4.5.2](https://getbootstrap.com/docs/4.5/getting-started/introduction/)** — grid system, navbar, jumbotron, and utility classes (vendored locally as `bootstrap.min.css`)
- **[Font Awesome 5.15.4](https://fontawesome.com/)** — icon font (vendored locally as `all.min.css`; not currently referenced with icon markup in the HTML)
- **Custom CSS** (`styles.css`) — brand colors, hero background overlay, custom scrollbar, and the "Register Now" button
- **External scripts (via CDN)**, loaded at the bottom of `emun.html`:
  - jQuery 3.5.1 (slim)
  - Popper.js 2.5.4
  - Bootstrap 4.5.2 JS bundle (powers the collapsible mobile navbar)

No custom JavaScript is written in this project — all interactivity (e.g. the responsive navbar toggle) comes from Bootstrap's bundled JS.

## Getting Started

Since this is a static site with no build step, you can preview it locally in a couple of ways:

### Option 1: Open directly in a browser
Simply open [emun.html](emun.html) in any modern web browser.

### Option 2: Serve locally (recommended, avoids any relative-path/CORS quirks)

Using Python:
```bash
python -m http.server 8000
```
Then visit `http://localhost:8000/emun.html`.

Using Node (with `npx serve`):
```bash
npx serve .
```

> Note: An active internet connection is required for full functionality, since jQuery, Popper, and the Bootstrap JS bundle are loaded from CDNs (see [emun.html:160-162](emun.html#L160-L162)).

## Page Sections

1. **Navbar** — Sticky top navigation with the CEME logo (linking to `ceme.nust.edu.pk`), the EMUN Instagram link, and anchor links to each page section. Collapses into a hamburger menu on small screens.
2. **Hero / Jumbotron** — Full-width banner with a background photo (`emephoto.jpg`), title, and tagline.
3. **About** — Two-column layout introducing the conference with the `EMUN'24.png` image, plus a blurred white overlay effect behind the section (`.jumbotron-custom-overlay`).
4. **Conference Details** — Dark-themed section containing the full invitation text, conference dates, and the five committees (UNSC, SPECPOL, DISEC, SSFT, PNA).
5. **Registrations** — Registration timeline (Early Bird: 14th–19th April 2024; Regular: after 19th April 2024) and a call-to-action button linking to the external registration site (`nustemeolympiad.pk`).
6. **FAQ** — Placeholder section; currently contains only a heading and intro line with no actual Q&A content yet.
7. **Contact** — Organizing committee contact cards (name, email, phone) for the President, Vice President, Chief of Staff, General Secretary, and Assistant General Secretary.
8. **Footer** — Copyright notice.

## Styling Notes

Key custom styles defined in [styles.css](styles.css):

- **`.bg-blue`** — Brand blue (`#005596`) used for the navbar and footer.
- **`.jumbotron-custom`** — Applies `emephoto.jpg` as a full-bleed background image for the hero banner.
- **`.jumbotron-custom-overlay`** — A semi-transparent, blurred white layer behind the "About" section for a frosted-glass effect.
- **`.navbar-logo`** — Fixes the CEME logo to the top-left of the viewport at a fixed size (170px wide).
- **Custom scrollbar** — Styled via `::-webkit-scrollbar` pseudo-elements (orange thumb `#fa9f42` on blue track `#005596`); this only works in WebKit/Chromium-based browsers.
- **`.register-btn`** — Yellow call-to-action button with a hover state, used for the "Register Now" link.

## Assets

| File | Used For |
|---|---|
| `EME-logo-revised.png` | Navbar brand logo (links to the CEME website) |
| `EMUN'24.png` | Image in the About section |
| `emephoto.jpg` | Hero/jumbotron background photo |
| `logo.svg` | Vector logo asset (not currently referenced in `emun.html`) |

> Note: `EMUN'24.png` contains an apostrophe in its filename, which is valid but worth being careful with when referencing it in code, shells, or URLs (it must be URL-encoded as `%27` if linked outside of an `<img src="...">` HTML attribute).

## Contact Information

As listed in the site's Contact section:

| Role | Name | Email | Phone |
|---|---|---|---|
| President | Bilal Tariq | mbilaltariq13@gmail.com | +92 302 5888848 |
| Vice President | Muhammad Salman | salmankhattak021@gmail.com | +92 345 4069556 |
| Chief of Staff | Ahmed Saeed | ahmed.saeed.study@gmail.com | +92 355 8432397 |
| General Secretary | Muhammad Hadi | hadimuhammad3112@gmail.com | +92 3458288723 |
| Assistant General Secretary | Furqan Ahmed Fareed | f6fareed004@gmail.com | +92 311 6455837 |

## Known Issues / Improvement Ideas

These are observations based on the current state of the code, useful if you plan to continue developing the site:

- **FAQ section is empty** — only contains a heading and one line of placeholder text; no actual questions/answers are implemented.
- **`logo.svg` and `all.min.css` (Font Awesome) are vendored but unused** — no `<img>` tag references `logo.svg`, and no `fa`/`fab`/`fas` icon classes appear in `emun.html`. Consider removing them if they stay unused, or wiring them in (e.g., social icons in the navbar/footer).
- **Hardcoded/dated content** — the conference dates (2–4 May 2024) and registration windows (April 2024) are now in the past; update or archive this copy for future events.
- **`z-index: -1` on `.jumbotron-custom-overlay`** ([styles.css:48](styles.css#L48)) pushes the overlay behind the section content, which may not match the intended "blurred overlay" visual — verify this renders as expected across browsers.
- **No `alt` text refinement** — image alt attributes are generic (e.g., `"Logo 1"`, `"About Image"`); consider more descriptive alt text for accessibility.
- **No favicon** is defined in the `<head>`.
- **CDN dependency** — jQuery, Popper, and Bootstrap JS are loaded from public CDNs at the bottom of the page; if offline support is needed, vendor these locally like `bootstrap.min.css`.
- **No `.gitignore` or dependency manifest** — since there's no build tooling, this is optional, but consider adding a `.gitignore` if any local/OS-specific files start getting created.

## Deployment

Because this is a purely static site, it can be deployed to any static hosting provider without a build step, for example:

- **GitHub Pages** — serve directly from the repository (point Pages at the branch/root, and consider renaming `emun.html` to `index.html` or configuring the default document).
- **Netlify / Vercel** — drag-and-drop or connect the repo; no build command needed.
- **Any traditional web host** — upload all files via FTP/SFTP to the public web root.

> If deploying as the site root, you likely want to rename `emun.html` to `index.html` (or configure your host to treat `emun.html` as the default document) so visiting the bare domain loads the page.

## License

No license file is currently included in this repository. All rights are reserved by the EMUN Conference organizing team unless otherwise specified.
