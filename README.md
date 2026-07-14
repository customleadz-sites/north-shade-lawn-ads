# North Shade Lawn — Google Ads Landing Pages

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

## Before it goes live — 3 things to wire up

1. **Form → Formspree.** In each page find `action="https://formspree.io/f/REPLACE_ME"`
   and paste your real Formspree endpoint. Add a hidden field so it returns to the
   thank-you page:
   `<input type="hidden" name="_next" value="https://YOURDOMAIN/thank-you.html">`

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
