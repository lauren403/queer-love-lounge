# Queer Love Lounge

Live site: **https://queerlovelounge.com.au**
Hosted on Netlify (project `bbc-queer-love-lounge`). Part of Body Belonging Clinic.

## How this deploys

This repo **is** the website. There is no build step — the files here are
served exactly as they are (`publish = "."` in `netlify.toml`).

Push to `main` → Netlify deploys. That's it.

Before August 2026 this site was updated by dragging a folder onto Netlify,
which meant the only copy of the site lived in whoever's Downloads folder had
it last, with no history and no way to undo a bad change. That is why it now
lives here.

## Editing

Change a `.html` file, commit, push. The change is live in seconds.

**Careful:** these pages are hand-written HTML with the CSS and JS inline in
each file. There is no template and no shared partial. If you change something
that appears on every page — the nav, the footer, the phone number, a fee —
you have to change it in **each** file that contains it. Search the whole repo
before assuming you're done.

## Structure

| Path | What it is |
|---|---|
| `index.html` | Homepage |
| `queer-couples-therapy-{city}.html` | Six city landing pages (Melbourne, Sydney, Brisbane, Perth, Adelaide, Canberra) |
| `couples-therapy-questioning-sexuality.html` | Topic page |
| `pull-up-a-chair-intensive.html` | Intensive offer |
| `relationship-tune-up.html` | Tune-up offer |
| `find-the-miss.html` | Quiz / lead magnet |
| `privacy.html` | Privacy policy (`noindex`) |
| `404.html` | Not-found page |
| `assets/*.webp` | Content-hashed images — filenames are the cache key, never rename them |
| `og-image.jpg` | Social share card (1200×630) |
| `sitemap.xml`, `robots.txt` | Search engine directives |
| `netlify.toml` | Hosting config: headers, caching, redirect |

## Facts that live in more than one place

Fees, session lengths and contact details are written into the visible copy
**and** repeated inside the JSON-LD `<script type="application/ld+json">`
blocks near the bottom of each page. Change one and you must change the other,
or the site will tell Google something different from what it tells a reader.

**Zanda is the source of truth for fees.** If this site and Zanda disagree,
Zanda is right and this site is wrong.

Current couples fees: first session $240 (90 min), ongoing $190 (75 min),
free 15-minute intro call $0, $50 deposit required, 48-hour cancellation.

## Third parties on these pages

- Google Fonts
- MailerLite (signup forms)
- GA4 `G-N15ZB01HCY` and Meta pixel `1558984099030206` — **consent-gated**:
  nothing loads until the visitor accepts the cookie banner. Keep it that way.
- Zanda client portal (booking links)

If you add another third party, widen the CSP in `netlify.toml` to match, or
it will be blocked once that policy is enforced.

## Contact

`lovelounge@queerlovelounge.com.au` (alias into the Body Belonging inbox).
