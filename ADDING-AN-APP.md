# Adding an app to the site

Maintainer notes. This file is not linked from the site.

The site is plain HTML and CSS served by GitHub Pages from `main` (repo root).
There is no build step; `.nojekyll` makes Pages serve files exactly as they are.

## Layout

```
index.html                 home page with the app list
404.html                   not-found page (uses root-absolute paths like /assets/…)
assets/site.css            shared stylesheet for every page
assets/logo.png            ThePixelForgeDev logo (header and home page)
assets/favicon.png         site favicon
assets/apple-touch-icon.png
<app-slug>/index.html      app page       → https://the-pixelforge-dev.github.io/<app-slug>/
<app-slug>/privacy/index.html  privacy policy → https://the-pixelforge-dev.github.io/<app-slug>/privacy/
<app-slug>/icon.png        app icon, square PNG, about 256×256
```

## Steps

1. **Pick a slug.** Short, lowercase and permanent, e.g. `blinkcam`. Its privacy
   URL goes into Play Console and usually into the app itself, so never rename it later.
2. **Copy an existing app folder:** `cp -r blinkcam <app-slug>`.
3. **Replace `<app-slug>/icon.png`** with the new app's icon.
4. **Edit `<app-slug>/index.html`:** the `<title>`, meta description, brand name,
   headline (tagline), description, feature list and status badge. Keep the site
   header and footer as they are.
5. **Rewrite `<app-slug>/privacy/index.html`** for the new app, covering its actual
   permissions and data use, and set the effective date. Don't copy BlinkCam's
   policy text unchanged.
6. **Add a card to `index.html`:** copy the `<li>` block inside `<ul class="app-list">`
   and change the slug, icon alt text, name, `id`/`aria-labelledby`, tagline,
   summary and badge. Newest or most important app first.
7. **Preview** in a browser (open `index.html` directly), including a phone
   width of about 360px, then commit and push.
8. **Check** after about 2 minutes that `/<app-slug>/` and `/<app-slug>/privacy/`
   return 200.

## When an app goes live

Replace the `Coming soon` badge on its home card and app page with a store link:

```html
<a class="badge" href="https://play.google.com/store/apps/details?id=PACKAGE_ID">Get it on Google Play</a>
```

## Rules

- No external fonts, scripts, analytics, trackers or CDNs. The privacy policies
  promise no tracking, so the site must not track anyone either.
- Pages use relative links (`../assets/site.css`), except `404.html`.
- Don't move or rename existing `/<app-slug>/` or `/<app-slug>/privacy/` URLs.
