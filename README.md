# North Shade Lawn — Google Ads Landing Pages

**LIVE at https://lp.northshadelawnllc.com** (deployed 2026-07-21 — Vercel project
`northshadelawnlp`, repo `customleadz-sites/north-shade-lawn-ads`, branch `master`).
Clean URLs: `/landscaping`, `/retaining-walls`, `/paver-patios`, `/thank-you`.
**Deliberately noindexed** (meta noindex,nofollow + robots.txt Disallow) so these ad
pages never compete with the main site in Google search — has zero effect on the main
site's SEO. Push to `master` = auto-deploy.

**Separate from the main marketing site.** These are standalone, single-goal conversion
pages built for the Google Ads campaign. They do **not** share the website's git repo or
Vercel project — this is a brand-new, self-contained folder.

## The pages (one per ad group)

| File | Ad group it serves |
|------|--------------------|
| `landscaping.html` | Landscaping — design & install |
| `retaining-walls.html` | Retaining Walls |
| `paver-patios.html` | Paver Patios & Walkways |
| `thank-you.html` | Shared form-confirmation page (the conversion goal) |

Each page: no nav, one goal (call or quote form), message-matched headline, real photos
only, 3 trust badges, reviews, guarantees, service area, FAQ, sticky mobile call bar.

## Preview locally

Just double-click any `.html` file, or open it in your browser. Everything works offline
except the fonts (they load from Google). Submitting the form locally sends you to the
thank-you page so you can see the whole flow.

## Before it goes live — 1 thing left to wire up

1. **Forms — DONE (2026-07-21).** Every page now has TWO live quote forms (hero +
   bottom of page), both posting to **Web3Forms** with the same access key as the
   main website's contact form → delivers to **northshadelawn23@gmail.com**.
   Each email arrives with subject "NEW GOOGLE ADS LEAD — [Service] Landing Page"
   plus a "Lead Source" line saying which page and which form (top/bottom), so the
   client always knows the lead came from Google Ads. Honeypot spam protection
   included. On success the visitor is sent to `thank-you.html` (the conversion
   page). Note: Web3Forms blocks headless/bot browsers — test by hand, not scripts.

2. **Conversion tracking.** Paste your Google Ads / GA4 `gtag.js` snippet where each page
   says `<!-- TODO(tracking) -->`, then swap the `AW-XXXX/call` and `AW-XXXX/form`
   placeholders (search `njCall` / `njSubmit`) for your real conversion IDs. Fire the
   form conversion on the thank-you page load too. **Tracking must work before spending.**

3. **Point each ad group's final URL at its matching page** (message match is the #1
   conversion lever — landscaping ads → landscaping.html, etc.).

## Notes

- Only one real review was available (Linda Jones). No review counts were invented.
  Add more Google reviews as they come in — the review strip and feature block are easy
  to duplicate.
- Photos are optimized copies of the client's real work (in `img/`). Originals live in
  `../assets/web-images/`.
- Fonts: Bricolage Grotesque + Instrument Sans (intentionally different from the main
  site's Fraunces + Hanken Grotesk).
