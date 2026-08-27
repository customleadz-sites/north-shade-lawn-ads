# North Shade Lawn — Landing Page Improvement Plan — 2026-08-27

Built from the 2026-08-27 Google Ads audit. The problem being solved: pages convert
~2.3% overall (healthy local pages do 10–15%), the two hardscape pages took 73 clicks /
$266 with zero leads, and Google rates landing-page experience BELOW_AVERAGE on nearly
every keyword — which is also feeding the 56.5% of impression share lost to ad rank.

The good news: the structure is already right (message-matched H1s, form in hero, sticky
call bar, before/afters, service-specific FAQs, no nav). Verified working: the
`?loc={loc_physical_ms}` final URL suffix IS set on the campaign, so the dynamic town
headlines are live. This is a tuning job, not a rebuild.

## 1. Page weight — the likely "below average" driver (all 3 pages) 🔴 biggest win

86% of ad clicks are mobile, and each page ships roughly **2–3 MB of images**:

- Heroes: `ls-hero.jpg` 582KB, `pp-hero.jpg` 547KB, `rw-hero.jpg` 335KB
- Each before/after slider pair: ~430–520KB per image, two sliders per page
- **`logo.png` is 384KB** (loads in the header on every page); `logo-white.png` 291KB in the footer

Fix (no visual change): convert everything to WebP sized to actual display dimensions
(heroes ~1600px, gallery ~800px, logos as small PNGs/SVG <20KB), add explicit
width/height to stop layout shift. Expect ~70–80% smaller pages. This is the item most
likely to move Google's landing-page-experience rating, which lifts Quality Score →
cheaper clicks → more impression share, on top of fewer people bailing before the page
paints.

## 2. Proof mismatch on the hardscape pages 🔴 the 0-conversion pages' gap

All three pages show the **same single review — and it's a landscaping review** (garden
tear-out, mulch, plants, from Linda Jones). A retaining-wall or patio shopper researching
a $5k–$15k job reads a gardening testimonial and one review total. That's the weakest
part of exactly the two pages that produced zero leads.

- Ask Dayne for 2–3 reviews from wall/patio/hardscape customers (even short texts he can
  get this week). Put wall reviews on the wall page, patio reviews on the patio page.
- Add the Google rating badge + review count if his GBP has reviews, linked or not.
- The hardscape pages' galleries should lead with finished walls/patios (verify current
  image picks) — the before/after of the failing wood wall is great; more like that.

## 3. Call-click tracking is still a stub (all 3 pages) 🟠 quick code fix

`njCall()` fires `send_to:'AW-XXXX/call'` — a placeholder that tracks nothing. Calls are
only being caught by Google's number-swap ("Call From Website"), which misses direct
tel-taps that don't go through the swapped number. Fix: point njCall at the real
click-to-call conversion label (or remove the stub so it stops sending a junk event).
While in there: the form conversion currently fires *before* Web3Forms confirms the send
— move the gtag call into the success path so failed sends don't count.

## 4. Faces on the page 🟠 cheap trust win

The "You'll deal with Dayne & William" section is strong copy with a `TODO(photo)`
comment where the photo should be — on all three pages. `img/ls-crew.jpg` already exists
in the folder (unused?). A real owner/crew photo next to that copy is one of the
highest-trust elements a local page can have. If Dayne can send a decent owners photo,
even phone-quality, use it.

## 5. Cost anchoring for hardscape (needs Dayne's numbers) 🟡 discuss first

"How much does a retaining wall cost"-type queries dominate the hardscape search terms,
and both FAQ answers dodge the number entirely. Big-ticket pages convert better with an
honest anchor: "Most walls we build run $X–$Y; every quote in writing before work
starts." Needs Dayne's real ranges and his OK — never invent numbers. If he won't give
ranges, a "typical projects" line (small garden wall vs. full terrace) with photos is the
fallback.

## 6. Add a text option 🟡 discuss

The ads run a "Call Or Text" callout, but the pages only offer call + form. Younger
homeowners especially will text before they'll call. If Dayne's number takes texts: add
an SMS link next to the call button on the sticky mobile bar. If it doesn't, pull the
"Call Or Text" callout from the ads instead — the promise should match the page.

## Not broken — leave alone

- Dynamic town headline (suffix verified set on the campaign)
- Form length (name + phone + message is right; don't add fields)
- Page structure, FAQs, message-matched H1s, noindex setup
- Landscaping page converts ~3.2% — it gets the same fixes but it isn't the emergency

## Order of work + measurement

1. Images/WebP pass (#1) + tracking cleanup (#3) — pure code, no client input needed
2. Owner photo (#4) + hardscape reviews (#2) — one ask to Dayne covers both
3. Cost anchors (#5) + text option (#6) — after talking to Dayne
4. Deploy, then judge on 3 weeks of data (one change-batch, then hands off): target is
   page conversion moving from ~2.3% toward 6%+ and LP experience ratings moving off
   below-average. At 6%+ the same $933 buys ~15 leads instead of 6.
