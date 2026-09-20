# Marriage Hall — Website

A static HTML/CSS/JS website for the Marriage Hall Android app (matrimonial application). Built for use as the Play Store developer website and for ad-verification (e.g. AppLovin MAX) purposes.

## Structure

```
marriage-hall/
├── index.html      Home page (hero, trust, how it works, features, screenshots, why us, download CTA)
├── about.html       About Marriage Hall
├── privacy.html      Privacy Policy (template — needs real details)
├── terms.html        Terms & Conditions (template — needs real details)
├── contact.html       Contact page with a front-end-only form
├── app-ads.txt         Placeholder — replace with your real app-ads.txt contents
├── css/styles.css       Shared design system and styles
├── js/main.js            Shared behavior (nav, scroll reveal, contact form)
└── images/                Empty — add real screenshots/photos here (see below)
```

Every page shares the same header, mobile nav, and footer markup (there's no build step, so these are duplicated per page — keep them in sync if you edit navigation).

## Before you publish — required edits

This site was intentionally built **without fabricated data**. You must fill in the following before it goes live:

1. **Google Play Store link** — search each HTML file for `href="#"` near `store-btn` / `footer-store` comments (marked `<!-- TODO -->`) and replace with your real Play Store URL.
2. **Support email** — replace every `support@example.com` placeholder (footer, contact page, privacy, terms) with your real support address.
3. **`app-ads.txt`** — replace the contents of `app-ads.txt` with the real file text supplied by your advertising provider(s). Do not invent entries.
4. **Privacy Policy (`privacy.html`)** — replace every `[bracketed placeholder]` with your actual data practices. Have it reviewed by a qualified professional for your jurisdiction.
5. **Terms & Conditions (`terms.html`)** — same as above: replace all `[bracketed placeholders]` (company name, jurisdiction, pricing, etc.) and have it reviewed legally.
6. **Canonical / Open Graph URLs** — every page has `https://YOUR-DOMAIN.com/...` placeholders in `<link rel="canonical">` and `<meta property="og:...">` tags. Replace `YOUR-DOMAIN.com` with your real domain.
7. **Screenshots** — the phone mockups on the site are illustrative UI recreations, not real app screenshots. If you'd like actual screenshots, add image files to `images/` and swap them into the `.phone-screen` markup (or replace the mockup blocks with `<img>` tags).
8. **Contact form backend** — `js/main.js` has a front-end-only handler for `#contact-form` with a comment marking where to wire up a real submission endpoint (email API, form service, etc.). Right now it only validates and shows a message; it does not send anything.
9. **Company/legal details** — no company registration numbers, addresses, certifications, partnerships, or user statistics have been included anywhere, per your instructions. Add only verified information if/where you want it to appear.

## Deployment

This is a plain static site — no build tools or dependencies required.

- **Any static host** (Netlify, Vercel, GitHub Pages, Cloudflare Pages, S3 + CloudFront, traditional shared hosting): upload the contents of this folder as-is.
- Make sure `app-ads.txt` is served at the site root (`https://YOUR-DOMAIN.com/app-ads.txt`) as **plain text** — most static hosts do this automatically for a `.txt` file at the root.
- Fonts (Fraunces, Inter) load from Google Fonts via `<link>` tags in each page's `<head>`. If you need a fully offline/self-hosted site, download the font files and update the `@font-face`/`<link>` references.

## Notes on design

- Palette: deep navy (`--navy-950`/`--navy-900`), light sky blue (`--sky-500`/`--sky-100`), warm champagne accent (`--champagne-500`) used sparingly, warm-white paper background.
- Type: Fraunces (display serif) for headings, Inter for body/UI text.
- All icons are inline SVG (no icon font/library dependency).
- Scroll-reveal and hover animations respect `prefers-reduced-motion`.
- Fully responsive from ~360px mobile up through desktop; mobile nav collapses into a full-screen panel.
