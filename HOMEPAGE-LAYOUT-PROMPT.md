# Homepage Layout Prompt — Aranyak Resort, Mukutmanipur

> Paste everything below the line into your AI site builder or hand it to a developer.
> It is written for the existing static site in this folder (`index.html`, `bn/index.html`, `images/`).
> Bracketed items like `[ADD: …]` are facts only the resort can supply — fill them or delete the line. Never let the builder invent them.

---

## 1. Role and goal

You are a senior hospitality UX designer and front-end developer. Redesign the homepage of **Aranyak Resort & Restaurant, Mukutmanipur** as a conversion-focused, boutique-luxury experience.

**Primary conversion:** a dated booking enquiry (check-in, check-out, guests, room type) sent to the resort on WhatsApp.
**Secondary conversions:** phone call, group-stay enquiry, restaurant / meal-plan enquiry.
**Success test:** a first-time visitor on a phone can go from landing to a sent, dated enquiry in under 5 seconds of interaction (3 taps + send), without scrolling.

Every section must do one of three jobs: **make them want it** (media), **make them trust it** (proof), or **let them act** (booking). Cut anything that does none.

## 2. Property facts (use only these — do not invent)

- Name: Aranyak Resort & Restaurant · Bengali: আরণ্যক · মুকুটমণিপুর
- Positioning line: *A garden stay among the trees, minutes from Mukutmanipur Dam.*
- Family-run, owner-managed. Bankura's red-soil country, Jungle Mahal edge.
- 25 rooms + dormitory. Room types: Deluxe Double (AC / non-AC), Deluxe Family (sleeps 4, AC / non-AC), Rustic Mud Cottage, Groups Dormitory (per-bed).
- ≈ 1 km to Mukutmanipur Dam and the Kangsabati reservoir. ≈ 250 km / 5–6 h from Kolkata. ≈ 55 km from Bankura Junction (pickup arranged).
- On site: restaurant (open to day visitors), free Wi-Fi, free parking, campfire & barbecue, garden & lawns, kids' play area, pickup & drop, sightseeing cars & toto.
- Experiences: sunset dam walk, boat to Bonpukuria deer park, Parasnath hill temple, Jhilimili & Sutan forest day trip, Ambikanagar.
- Tariffs: **on request, seasonal** — there are no published prices and no live inventory.
- Booking channel: WhatsApp / phone **+91 91633 95263** (`wa.me/919163395263`), alt +91 82402 71288, email aranyakmmpur@gmail.com.
- Address: Dam Road, near Sports Academy, Mukutmanipur, Bankura, West Bengal 722140.
- Group proof: 50+ guests hosted in one booking.
- Real guest quotes (Tripadvisor, keep verbatim, keep the dates):
  1. "Staff were polite and always ready to help, the owner is down to earth, and they booked us a car for Jhilimili and Sutan." — Family stay, July 2024
  2. "We booked for a 50-person corporate trip. The owner managed everything himself and the whole team went home happy." — Business trip, July 2024
  3. "Well-ventilated rooms with working AC, tasty food and well-behaved staff. The resort feels part of the forest around it." — October 2021
- `[ADD: Tripadvisor rating + review count, Google rating + review count — exact figures and the date checked]`
- `[ADD: years operating / established year]`
- `[ADD: any certification, tourism-board listing or award — only if real]`

## 3. Hard constraints

- **Static site, no backend.** The availability widget cannot query live inventory. It must *collect* the stay details and hand them to WhatsApp as a pre-filled, structured message. Label it honestly: "Check availability" → result "We'll confirm availability & best rate on WhatsApp, usually within `[ADD: response time, e.g. 1 hour, 8am–10pm]`."
- **Bilingual.** Everything ships in English (`/`) and Bengali (`/bn/`). WhatsApp messages are generated in the visitor's page language. Bengali uses Tiro Bangla / Hind Siliguri with looser line-height (1.75).
- **Keep the brand system** already in `index.html`: tokens `--ground #f2f5ec`, `--paper #fbfcf8`, `--ink #1c2716`, `--forest #35601d`, `--leaf #8cc63f`, `--bark #6b3e1b`, `--water #2e6c78`; display font Rozha One, body Hind; full dark-mode token set. Keep the logo files `images/aranyak-logo.webp` / `aranyak-mark.webp`.
- **Use the resort's own photos only** from `images/` (each has a full and `-sm` version). No stock photography, no AI-generated room images.
- No fake urgency ("Only 2 rooms left!"), no countdown timers, no invented ratings, no invented awards. Luxury guests read these as cheap; Aranyak can't back them up.

## 4. Luxury visual language ("boutique luxury" for a forest resort)

Luxury here means **calm, space and craft**, not gold and marble.

- Generous whitespace: section padding `clamp(72px, 10vw, 144px)` vertical. One idea per screen.
- Large, edge-to-edge photography; text never sits on busy image areas without a soft gradient scrim.
- Typography does the luxury work: Rozha One headlines at large sizes with tight leading (1.05–1.1); small uppercase eyebrows in `--bark` with 0.14em tracking; body copy max 62ch.
- Palette restraint: 90% neutrals (`--ground`, `--paper`, `--ink`), `--forest` reserved for primary actions, `--bark` for small accents. No more than one filled button visible per viewport (besides the sticky bar).
- Motion: slow and quiet — 400–600 ms fades, subtle 1.03 image scale on hover, no parallax on mobile, everything disabled under `prefers-reduced-motion`.
- Copy voice: warm, specific, unhurried, first-person plural ("we'll light the fire"). Concrete sensory detail over adjectives ("reservoir fish curry on a sal-leaf plate", not "exquisite cuisine").

## 5. Global component: Sticky "Book Now" bar

Present on every scroll position after the hero widget leaves the viewport. It is the single most important element on the page.

**Desktop (≥ 900 px)** — slim bar fused into the sticky header (height 64–68 px, blurred `--ground` at 88% opacity):
- Left: logo mark + "Aranyak".
- Centre (appears only once the hero widget scrolls out): compact inline widget — `Check-in · Check-out · Guests` as three pill buttons that open the same date/guest pickers as the hero widget, state shared.
- Right: **Book Now** (filled `--forest`, pill) + phone icon button (`tel:+919163395263`) + language toggle (বাংলা / EN).
- Nav links (Rooms, Experiences, Dining, Groups, Location) collapse into a "Menu" button when the compact widget is showing, so the bar never wraps.

**Mobile (< 900 px)** — bottom-anchored action bar (thumb zone), 64 px + `env(safe-area-inset-bottom)`:
- Two-thirds width: **Book Now** (filled) — shows selected dates if already chosen, e.g. "Book · 14–16 Dec · 2 guests".
- One-third: WhatsApp icon button + Call icon button.
- Top header on mobile shrinks to logo + language + menu, and hides on scroll-down / reappears on scroll-up.
- Hide the bottom bar while the hero widget, the booking sheet, or the footer contact block is in view (no duplicate CTAs on one screen).

**Behaviour:** tapping Book Now opens the booking sheet (bottom sheet on mobile, anchored popover on desktop) pre-filled with any dates already chosen. Never navigates away.

## 6. Global component: 5-second availability widget

Lives in the hero (full form), in the sticky bar (compact), and in the booking sheet. One shared state object; changing dates in one updates all.

**Fields (in this order, all visible at once):**
1. **Dates** — single range picker, one control for check-in → check-out. Default: today + 7 → today + 9 (Friday–Sunday if within reach). Disable past dates. Show nights count live ("2 nights").
2. **Guests** — stepper (Adults 1–8, Children 0–6), default 2 adults. If guests > 8, swap the button label to "Plan a group stay" and route to the group flow.
3. **Stay type** (optional, collapsed chips) — Double · Family · Mud Cottage · Dormitory · "Help me choose" (default).
4. **Button: Check availability** (filled, full-width on mobile).

**Five-second budget:** defaults are pre-filled, so the fastest path is literally *tap Check availability → tap Send in WhatsApp*. Target ≤ 3 taps for a visitor who changes dates.

**On submit:**
- Validate inline (no alerts). Check-out must be after check-in.
- Show a confirmation micro-step inside the widget (not a new page): summary card "14 Dec → 16 Dec · 2 nights · 2 adults · Deluxe Double" + two buttons: **Send on WhatsApp** (primary) and **Call instead**.
- WhatsApp deep link `https://wa.me/919163395263?text=` with a URL-encoded, structured message in the page language:
  ```
  Hello Aranyak, I'd like to check availability.
  Check-in: Sat 14 Dec 2026
  Check-out: Mon 16 Dec 2026 (2 nights)
  Guests: 2 adults, 0 children
  Stay: Deluxe Double (AC)
  Sent from resortsaranyak.com
  ```
  Bengali version mirrors this with Bengali labels and Bengali-formatted dates.
- Under the button, one reassurance line: "No payment now · Best rate direct · Reply within `[ADD]`."

**Accessibility:** native `<input type="date">` fallback on devices where the custom picker fails; full keyboard support; `aria-live="polite"` for the nights count and validation; 44 px minimum targets.

## 7. Homepage structure (top to bottom)

For each section: **job → content → layout (desktop / mobile) → CTA**.

### 7.0 Header
As specified in §5. Transparent over the hero on first load (white logo variant / light text with scrim), solidifies on scroll.

### 7.1 Hero — "Want it + act now" (above the fold)
- **Content:** eyebrow "আরণ্যক · মুকুটমণিপুর"; H1 "A garden stay among the trees, minutes from Mukutmanipur Dam"; one-line lede "Family-run rooms, mud cottages and Bengali home cooking, 1 km from the Kangsabati reservoir."
- **Media:** full-bleed image, 100svh desktop / 72svh mobile. Lead image `images/reservoir-islands.webp` (or `garden-walkway.webp` — A/B test). Optional muted 8–12 s ambient loop later `[ADD: video if shot]`; poster image always first. Preload the hero image (`fetchpriority="high"`), serve `-sm` under 700 px.
- **Widget:** full availability widget (§6) on a `--paper` card, bottom-left on desktop overlapping the image edge by ~40 px; on mobile it sits directly under the image, above the fold on a 390×844 screen.
- **Micro-trust under widget:** a single line of 3 icon facts — "1 km to the dam · Free pickup on request · Owner-run since `[ADD]`".
- **CTA:** the widget button is the only filled button in the hero. Secondary text link: "Or WhatsApp us →".

### 7.2 Trust strip — "Trust it, instantly"
- Thin band directly below the hero, `--band` background, 72–88 px tall.
- 4–5 items in a single row (horizontal scroll-snap on mobile, no wrapping):
  - `[ADD: Tripadvisor ★ x.x · N reviews]` with logo mark, linking to the listing
  - `[ADD: Google ★ x.x · N reviews]`
  - "50+ guests hosted in one booking"
  - "25 rooms + dormitory"
  - "Restaurant on site · open to day visitors"
- Rule: if a figure isn't supplied, drop that item — never placeholder a rating.

### 7.3 Signature media grid — "Want it"
- **Job:** show the place in 6 seconds of scrolling. This replaces a long gallery.
- **Layout (desktop):** asymmetric bento grid, 12-column, 3 rows, 8 px gutters, `--r` radius:
  - A (span 7 × 2 rows): `garden-walkway.webp` — "The garden walk"
  - B (span 5 × 1): `colourful-cottages.webp` — "Cottage row"
  - C (span 5 × 1): `campfire.webp` — "Campfire nights"
  - D (span 4 × 1): `thatched-cottage.webp` — "The mud cottage"
  - E (span 4 × 1): `garden-cafe-night.webp` — "The garden café after dark"
  - F (span 4 × 1): `bengali-meal.webp` — "Lunch on a sal-leaf plate"
- **Mobile:** 2-column masonry, first image full-width, max 6 tiles, then a "See all 30+ photos" button.
- Caption appears on hover/focus (desktop) and always beneath (mobile), small Hind 0.9rem.
- Tap opens a full-screen lightbox with swipe, keyboard arrows, captions, and a persistent **Book these dates** button in the lightbox footer (conversion inside the gallery).
- Aspect ratios fixed with `aspect-ratio` to prevent layout shift; `loading="lazy"`, `decoding="async"`, `srcset` with `-sm` / full.

### 7.4 Rooms & stays — "Want it + act"
- Heading: "Four ways to stay, from couples to a busload."
- 4 cards in a row (desktop) / horizontal snap carousel with peeking next card (mobile).
- Each card: photo carousel (3–6 images, dot indicator, from `room-double-*`, `room-family-*`, `room-ac-*`, `thatched-cottage`), eyebrow (e.g. "AC or non-AC · Sleeps 4"), name, 3 feature lines with icons, "Best for families" tag, price line "Tariff on request · best rate direct", and **Check dates for this room** button that opens the booking sheet with Stay type pre-selected.
- Dormitory card links to the group flow (§7.8). `[ADD: real dormitory photo — currently an illustration]`.
- Below the cards: amenity icon row (Wi-Fi, parking, restaurant, campfire, play area, pickup, sightseeing).

### 7.5 Experiences — "Want it"
- Heading: "Campfire evenings, boat rides and forest drives."
- Editorial split layout: large image left (`dam-road.webp` / `reservoir-shore.webp`), list of 5 experiences right, each with a distance/time tag ("≈ 1 km", "Full day"). Mobile: image on top, list below.
- CTA: ghost button "Plan your days with us" → WhatsApp with "I'd like help planning sightseeing" pre-filled.

### 7.6 Dining — "Want it + secondary conversion"
- Full-bleed image band (`grilled-chicken.webp` or `dining-hall.webp`) with overlaid heading "Bengali home cooking, and a barbecue after dark."
- Below: "A day at the table" timeline (Breakfast → Lunch → Evening → Barbecue → Dinner) as a horizontal row of 5 small image-led steps; note "Sample only — the day's menu follows the market."
- CTA: "Reserve a table or meal plan" (ghost) → WhatsApp with dining message pre-filled. Line: "Driving back from the dam? Day visitors welcome for lunch."

### 7.7 Guest notes — "Trust it, deeply"
- Heading: "What guests tell us."
- 3 large pull-quote cards using the exact quotes in §2, each with trip type, date and "via Tripadvisor" linking to the review source.
- Above the quotes, an aggregate score block `[ADD: ★ rating, review count, "as of" date]` — omit entirely if not supplied.
- Desktop: 3 columns. Mobile: snap carousel, one quote per screen.
- CTA below: "Read all reviews on Tripadvisor ↗" (text link) + Book Now button.

### 7.8 Groups — "Secondary conversion"
- `--forest` background band, `--on-forest` text — the one dark/full-colour moment on the page.
- Heading: "Corporate outings, school trips and family reunions." Stat pair: "50+ guests in one booking" · "25 rooms + dormitory". Line: "The owner plans group stays personally."
- Mini form: Group size (select: 10–20, 20–50, 50+), Dates, Purpose (Corporate / School / Family / Other) → **Plan a group stay** → WhatsApp with structured group message.

### 7.9 Location — "Remove the last objection"
- Split: left — 3 distance stats (≈ 250 km from Kolkata, 5–6 h; ≈ 55 km from Bankura Jn, pickup arranged; ≈ 1 km from the dam) + address + "Open in Google Maps ↗"; right — static map image or click-to-load Google Maps embed (don't load the iframe until tapped — performance).
- CTA: "Arrange a pickup" → WhatsApp pre-filled.

### 7.10 FAQ — "Objection handling + SEO"
- 5–6 accordions: How do I book? · How far from the dam? · Is food available? · Pickup & sightseeing? · Large groups? · `[ADD: check-in/check-out times, cancellation policy, pets, payment methods]`.
- Mark up with `FAQPage` JSON-LD. Keep existing `LodgingBusiness` / `Hotel` schema; add `aggregateRating` only with real figures.

### 7.11 Final booking band — "Last chance to act"
- Full-bleed `pavilion-night.webp` with dark scrim, centred heading "The fire's lit at seven. Tell us your dates." + full availability widget repeated (shared state).
- Hide the sticky bottom bar while this is in view.

### 7.12 Footer
- Logo, address, all three contact routes as tap targets, language toggle, nav repeat, social links `[ADD]`, small print "Tariffs vary by season; we confirm the best rate directly."

## 8. Performance & media budget

- LCP < 2.0 s on 4G mid-range Android; CLS < 0.05; INP < 200 ms.
- Total homepage weight < 1.8 MB on mobile first load (lazy-load everything below the media grid).
- All images WebP (AVIF optional), fixed `width`/`height` or `aspect-ratio`, `srcset` with `-sm` (≈700 px) and full (≈1600 px). Ask for 2400 px originals for the hero and bento tile A.
- No carousel library heavier than 10 KB; prefer CSS scroll-snap. No jQuery.
- Fonts: preload Rozha One + Hind 400/600 subsets; `font-display: swap`; Bengali fonts load only on `/bn/`.

## 9. Accessibility

- WCAG 2.2 AA contrast in light and dark modes, including text on image scrims.
- Skip link, semantic landmarks, one `<h1>`, logical heading order.
- Every image has a descriptive `alt` in the page language; decorative ones `alt=""`.
- Sticky bars must not cover focused elements (`scroll-padding-bottom` equal to bar height).
- All interactions keyboard-operable; focus ring `3px solid var(--leaf)`.

## 10. Measurement (conversion instrumentation)

Fire analytics events (GA4 or Plausible) for:
`widget_dates_changed`, `widget_submit`, `whatsapp_booking_sent`, `call_tap`, `sticky_book_tap`, `room_card_check_dates` (with room type), `gallery_open`, `lightbox_book_tap`, `group_enquiry_sent`, `dining_enquiry_sent`, `lang_switch`.
Tag each WhatsApp message with a short source code (e.g. `ref:hero`, `ref:sticky`, `ref:room-family`) so the resort can tell which CTA produced a booking.

## 11. Acceptance checklist

- [ ] On a 390×844 phone, the hero image, H1 and a usable availability widget are all visible without scrolling.
- [ ] Landing → WhatsApp opened with a dated, structured message in ≤ 3 taps using defaults.
- [ ] A Book Now control is reachable from every scroll position, never more than one primary CTA per screen.
- [ ] Booking state (dates, guests, room) persists across hero widget, sticky bar, room cards, booking sheet and final band.
- [ ] English and Bengali pages are complete, with WhatsApp messages in the matching language.
- [ ] Every rating, number and quote on the page traces to §2 or to a filled `[ADD]` item. Nothing invented.
- [ ] Light and dark modes both pass contrast; reduced-motion respected.
- [ ] Lighthouse mobile: Performance ≥ 90, Accessibility ≥ 95, SEO ≥ 95.

## 12. Do not

- Do not show "Book Now" as a link to a page that doesn't exist or a payment form — there is no payment backend.
- Do not display prices, discounts or "lowest price guaranteed" claims.
- Do not use stock or AI imagery, fake scarcity, pop-up modals on entry, or auto-playing sound.
- Do not hide the phone number — many guests in this market prefer to call.
