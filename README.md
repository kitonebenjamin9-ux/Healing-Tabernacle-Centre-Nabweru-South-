# Healing Tabernacle Website — Customization Guide

Plain HTML/CSS/JS. No frameworks, no build step — just open `index.html` in a browser, or upload the whole folder to any web host.

## 1. Edit these files first
| File | What it controls |
|---|---|
| `js/config.js` | Church name, tagline, pastor info, contact details, service times, social links, livestream URL, nav menu, admin login credentials. Editing this updates the header/footer/text automatically on **every** page. |
| `css/style.css` | All colours (top of file, in `:root`), fonts, spacing. Change a few CSS variables to re-theme the whole site. |
| `css/admin.css` | Admin panel colours/layout (separate token set, at the top of the file). |

## 2. Replace images & video
Every image/video has a `<!-- CHANGE ... HERE -->` comment right above it in the HTML. Placeholder files are already in place so nothing looks broken — just replace the file at the same path (or update the `src`/`href`):

- Logo: `assets/logo/church-logo.png`
- Pastor photo: `assets/images/pastor.jpg`
- Hero background video: `assets/videos/hero-video.mp4`
- Hero fallback image: `assets/images/hero.jpg`
- Gallery photos: `assets/images/gallery-1.jpg` … `gallery-7.jpg`
- **Featured gallery photo** (e.g. a specific member's photo): `assets/images/gallery-featured-member.jpg` — used on `gallery.html`
- Sermon thumbnails: `assets/images/sermon-1.jpg`, `sermon-2.jpg`, `sermon-3.jpg`
- Ministry photos: `assets/images/ministry-*.jpg`

All current images/video are labeled placeholders generated for this build — swap them for your real photos.

## 3. The admin panel
`admin/` is a front-end-only demo (login: `admin` / `healing2026`, set in `js/config.js`). It stores events/sermons/gallery/ministries in the browser's `localStorage` so you can test full add/edit/delete workflows. **It is not yet connected to the public pages or a real database** — see the notes inside `js/admin.js` and on each admin page for how to wire it up to a real backend when you're ready to go live with multiple admins.

## 4. What's new in this update
- **Colours**: retheme to royal blue / gold / white / cream (edit `--color-*` in `css/style.css`, and `--admin-*` in `css/admin.css`).
- **Give page**: `give.html` links to `giving-mtn.html`, `giving-airtel.html`, `giving-bank.html` — each with placeholder numbers/account details marked `<!-- CHANGE ... HERE -->`. Tap "Copy" to copy any number/account.
- **Clickable ministries**: cards on `ministries.html` now link to their own info pages: `children.html`, `youth.html`, `worship.html`, `outreach.html`, `men.html`, `women.html`.
- **New pages**: `pastors.html`, `testimonies.html`, `faq.html`, `404.html` — all use accordions/cards to reveal "more info" on click.
- **New folders**: `data/` (seed JSON, unused until wired to a real backend), `icons/` (social SVGs), `documents/` (add your PDFs here). `css/animations.css` and `css/responsive.css` are additive and only linked on the new pages above. `js/navigation.js`, `slider.js`, `gallery.js`, `events.js`, `livestream.js` are scaffold files for future features — not yet linked anywhere.
- Nav menu now includes **Give**; footer now includes **Pastors, Testimonies, FAQ, Give Online** (pointed at `give.html`).

## 4b. Structure
```
healing-tabernacle/
├── index.html, about.html, events.html, sermons.html,
│   gallery.html, ministries.html, contact.html, livestream.html
├── admin/         (separate login-protected panel)
├── css/           (style.css = public site, admin.css = admin panel)
├── js/            (config.js = settings, main.js = public site, admin.js = admin panel)
└── assets/        (images/, videos/, logo/)
```
