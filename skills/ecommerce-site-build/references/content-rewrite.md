# Optional phase: product content migration & copy rewrite

Use when the user wants product descriptions rewritten, terminology unified or product page content reorganized. It runs through the same gates as the page design:

- "Set the standard" happens around G1;
- the 3 pilot products are the G3 pilot product pages;
- the batch rewrite runs with the page rollout after G4 sign-off.

## 1. Set the standard before writing

- **Find an authority**: industry standards, official glossaries, the brand's own style sheet. If none exists, build one with the user.
- **Run a peer word-frequency check**: sample product pages from English-language sellers in the same category in the target market and count the descriptive terms they use. Find which phrases are industry standard and which are stiff literal translations or borrowed from another category (e.g. wine vocabulary for tea).
- **Turn it into a rules table**, each rule stating:

  | Don't use | Use instead | Why | Example |
  |---|---|---|---|

  The "why" matters: it lets you handle words that aren't in the table.
- **Common general rules**: cut empty superlatives like perfect / ultimate / amazing; cut unprovable health or certification claims; use one spelling for each concept across the whole site.

## 2. Pilot 3 products

- Pick 3 representative products and show a **sentence-by-sentence before / after**.
- **Wait for the user's approval before batching.** This is the step most often skipped, and skipping it causes the most rework.

## 3. Batch + read-back verification

- Back up all original text first; read each item back afterward and compare; change only what the rules cover.
- **Transform text with code** (replacements, HTML parsing), not by having the model retype the full text: retyping introduces typos (it has happened: a Chinese character silently swapped for a look-alike).
- **Overly broad cleanup rules delete real content** (it has happened: removing image captions also removed a sentence of body text), so check every cleanup rule's diff on the pilots first.
- Factual issues found along the way (conflicting years, suspicious numbers, inconsistent name spellings) **go on a list** for the user to decide.

## Structuring product page content

- **Descriptions are text only**; move images in descriptions into the product gallery. Deduplicate first: perceptual hashes alone miss cropped or framed copies, so use feature-point matching plus a human look at thumbnails.
- **Make reusable content structured data**, not HTML pasted into every product:
  - **Creator reviews**: a metaobject (creator, format, title, link, summary, date, image) + a product metafield reference, rendered by the template. For YouTube use a normal lazy-loaded iframe, not an auto-playing "lite" facade (it shows "Video unavailable" in some environments).
  - **Specs, origin, certifications**: metafields, so they double as collection filters.
- **Map relationships precisely**: attach a review video only to the products it actually covers (e.g. only the raw tea, not the ripe tea or blend from the same series), and show the user the product list before attaching.
