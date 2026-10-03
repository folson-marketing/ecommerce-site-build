# Site structure reference (D2C / cross-border e-commerce)

Design directions and pilot pages follow this structure. For a redesign, what the user said must not change takes priority; use this to find gaps. Sources are mainly Baymard Institute's e-commerce UX research and Shopify's official cross-border guidance.

## Global

- **Announcement bar**: the single most important promise (free-shipping threshold, dispatch time); can rotate 2–3 messages.
- **Header**: logo, main navigation (no more than ~7 top-level items, ~10 or fewer subcategories per level, top-level items clickable too), search, account, cart, currency / language switcher.
- **Footer**: Shop (main categories), Help (shipping, returns, FAQ, contact, order tracking), About (brand story, blog, wholesale / partnerships), Legal (privacy, terms, refunds, shipping policy), newsletter signup, social, payment icons.

## Home page (top to bottom)

1. Hero: one-line value proposition + primary button (to the hero collection) + secondary button (e.g. samples / starter product)
2. Trust bar: review score and count, free shipping / returns promise, origin or craft selling points (3–4 items)
3. Best sellers
4. Shop by category (a representative image per category)
5. Brand story / proof of craft (split image-text, with verifiable details)
6. New arrivals or featured collection
7. Education / how to use
8. Real reviews or UGC (only real reviews from the review app)
9. Press / partnerships (only if real)
10. Blog posts
11. Newsletter signup

Don't overload the home page with promo slots; carousels rotate every 5–7 seconds, and auto-rotation is off on mobile.

## Collection page (PLP)

- Title + 2–3 line intro (long SEO copy goes below the product grid)
- Filters: sidebar on desktop, drawer on mobile; multi-select within a filter; show applied filters with one-click clear
- Sort at least by: best selling, newest, price, rating
- Product cards: second image on hover, price, stars and review count, quick add; variants of the same product merged into one card
- Unit price for multi-size products (per gram / per piece)

## Product page (PDP) — where conversion happens

- **Gallery**: at least 3 images including one that shows scale; video optional
- **Buy box (above the fold)**: title, stars + review count (links to reviews), price, variant buttons instead of dropdowns, add to cart + express checkout, shipping cost / free-shipping threshold next to the button, estimated delivery, returns policy
- **Key benefits row**: 3–4 icon + short-phrase items (origin, specs, certifications, etc.)
- **Description**: text only, clearly sectioned; images go in the product gallery, not inside the description
- **Specs table**: structured attributes (metafields recommended, for filtering and reuse)
- **How to use / FAQ**
- **Reviews**: real reviews, reply to negative ones; review photos browsable across reviews
- **Creator reviews / UGC** (if any): KOL videos and blog reviews in their own section below the description, with a jump link from the buy box
- **Pairs well with / related products**
- **Sticky add-to-cart bar on mobile**
- **Structured data**: Product JSON-LD (price, availability, rating)

## Cart and checkout

- Slide-out cart drawer with a "spend $X more for free shipping" progress bar, cross-sells and express checkout.
- Show total cost early: Baymard data shows about 39% of abandonments are due to extra costs (shipping, tax, fees) appearing too late, and 19% to being forced to create an account. So allow guest checkout and state shipping on the PDP and in the cart.

## Content and trust pages

- About (brand story, founder, timeline, origin / factory photos)
- Blog (tutorials, buying guides, with products embedded)
- FAQ, Contact (response time, email), order tracking
- Wholesale / B2B inquiry, creator / affiliate program, loyalty program (as the business needs)

## Cross-border

- Multi-currency (Shopify Markets, etc.) with price-rounding rules
- Duties and taxes: DDP (delivered duty paid) or DDU (paid on delivery), stated in the shipping policy and the cart
- Shipping rates and delivery times by region
- Local payment methods
- Multi-language: subfolders (`/en-gb/`) + hreflang; translations use the terms locals actually search for
- Privacy compliance: cookie consent banner (GDPR); privacy policy covering the target markets' laws (GDPR / CCPA / PIPEDA, etc.)
- No unprovable claims (health benefits, certification words like "organic"); these carry risk on overseas ad platforms and under consumer protection law

## Tracking and SEO

- Exactly one source per event (e.g. GA4 via the official app, GTM via a custom pixel); confirm purchase events aren't double counted before launch
- One H1 per page; meta titles and descriptions; image alt text
- 301 redirects for any URL that changes in a redesign
- noindex pages like `/collections/all`
