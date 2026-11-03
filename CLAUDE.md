# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

Arif Durgeç's personal portfolio site, served by GitHub Pages from the `main` branch of `arfdrgc/arfdrgc.github.io` on the custom domain `arifdurgec.com` (`CNAME`). It is plain static HTML/CSS/JS: there is no build step, package manager, linter or test suite. Pushing to `main` deploys.

To preview locally, serve the folder over HTTP (some vendor scripts behave differently over `file://`):

```sh
python3 -m http.server 8000   # then open http://localhost:8000
```

## Structure

- `index.html` is the whole site: a single page with a header, `#hero`, `#about`, `#portfolio` and a footer. It is built on the BootstrapMade "Folio" template (Bootstrap 5.3).
- `assets/css/style.css` and `assets/js/main.js` are the template's files, lightly customised. `main.js` wires up the vendor libraries in `assets/vendor/` (Bootstrap, GLightbox, Isotope, Swiper, Typed.js, Bootstrap Icons, Boxicons). These are committed copies, not npm dependencies, so don't edit them.
- `<app-name>/privacy-policy.html` and `<app-name>/terms-conditions.html` (`happy-new-sort/`, `tabata-omniTimer/`, `the-mancala-game/`) are standalone pages with inline styles. They don't use the site's CSS or JS. App store listings link to these URLs, so **don't rename or move these folders or files**.
- `app-ads.txt` (AdMob publisher verification) and `google6d590ad815947cc0.html` (Google Search Console verification) must stay at the site root, unchanged.

## Adding or editing portfolio items

Every project is a hand-written `.portfolio-item` block inside `.portfolio-container` in `index.html`. Copy an existing block and keep these coupled pieces consistent:

- **Filter class**: `filter-app` (Gaming), `filter-training` or `filter-dancing`. These must match the `data-filter` values on the `#portfolio-flters` list, because Isotope filters on them in `main.js`.
- **Image**: put it in `assets/img/projects/`. The same path appears twice: in the `<img src>` and in the `.portfolio-lightbox` link's `href`. Lightbox links that share `data-gallery="portfolioGallery"` form one browsable gallery.
- **Optional `.details-link`**: an external link (Play Store, App Store or YouTube) with a Boxicons icon (`bxl-play-store`, `bxl-youtube`, `bxs-planet`).
- **Order**: items are listed newest first within each category, with Gaming first.
