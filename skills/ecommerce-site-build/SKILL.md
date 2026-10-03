---
name: ecommerce-site-build
description: Build a new e-commerce / D2C storefront or redesign an existing one end to end — requirements, asset collection, HTML design directions, pilot pages, sign-off, batch rollout and post-launch QA — controlled by 5 explicit user-approval gates, never touching the live site, backing up before every write and reading back after. Works with Shopify, static HTML, WordPress / WooCommerce, Shopline / Shoplazza and others. Includes an e-commerce site structure reference (home, collection, product page, cart, cross-border, tracking and SEO) and an optional product-copy rewrite and content migration phase. Use for building a Shopify or independent store, switching themes, redesigning product pages, or bulk-rewriting product descriptions.
---

# E-commerce Site Build & Redesign

Take a storefront from requirements to launch, or redesign an existing store in whole or in part. The workflow is built around **5 approval gates**; the work happens between gates.

This process comes from a real Shopify redesign (hundreds of products, a theme switch, product page rewrites, a creator-review section). The single biggest lesson: **finish each step, show it to the user, and wait for an explicit "confirmed" before moving on.** In that project the pilot product was rolled out to every product before the user had approved it. The user's words: "confirm with me once you finish the pilot product."

This is the English edition. A Chinese edition for Chinese-speaking teams is available as `ecommerce-site-build-zh`.

```
G0 Requirements → G1 Assets ready → G2 HTML direction chosen → G3 Pilot pages approved → G4 Sign-off → Batch rollout → Post-launch QA
```

Every gate needs the user's **explicit approval** in the conversation (a multiple-choice question is the easiest way). Without it, stop and wait; don't "get started in the meantime". If the user is away, finish the prep work, write down exactly what they need to decide, and stop at the gate.

## Tools: use capabilities, not fixed tool names

This skill runs in different agents (Claude.ai, Claude Code, ChatGPT, Codex and others), and each exposes different tools. Instructions below describe a **capability**. Use whichever tool provides it; if none does, use the fallback.

| Capability | Use | Fallback when missing |
|---|---|---|
| Ask the user | A structured multiple-choice tool (AskUserQuestion in Claude) | Ask in chat with a numbered list of options |
| Publish a shareable page | Artifact / Canvas or any tool that produces a web link (prefer a Design type if offered) | Deliver a self-contained `.html` file to open locally or deploy |
| Store admin | Shopify connector / Admin GraphQL; the platform's API or MCP | Browser (the user logs in); or export CSV for the user to import |
| Static deploy | Vercel / Netlify / GitHub tools | Hand over the code bundle for the user to deploy |
| Browse & screenshot | Any browser-automation tool | Ask the user to open the page and send screenshots or text |
| Connector discovery | A tool that searches or suggests MCP servers / connectors | Tell the user exactly what to install and which permissions it needs |
| Progress log | Project docs, memory, files in the repo | Output the progress log in chat for the user to save |

When a capability is missing, say what's missing and what the fallback is, and let the user choose: **install it**, **use the fallback**, or **pick a different option**. Never stall silently.

## Principles that apply throughout

1. **Never touch the live site.** Work in drafts, copies or preview environments (duplicate an unpublished Shopify theme; deploy HTML to staging). The user clicks publish.
2. **Back up, then write, then read back.** Before every batch write, export the original data (JSON / CSV). After writing, read the data back from the system and compare it to the target item by item. An API "success" response is not proof.
3. **Never invent anything.** Reviews, certifications, numbers, press mentions and founder stories come only from the user or a source you can cite. If you can't find it, mark it **[TO BE SUPPLIED BY USER]**. Fake reviews or certifications on a store are a compliance problem, not just a quality problem.
4. **Flag out-of-scope issues; don't fix them.** You'll find other problems along the way (contradictory facts, typos, inconsistent data). List them in an "Open questions" list for the user; don't quietly change them.
5. **Use a consistent prefix** for everything you create (theme names, sections, metafields, automations) so the user can see at a glance what the agent made.
6. **Log decisions.** Keep a progress doc: the choice at each gate, the date, backup locations, to-dos. If there's a Project, keep it there so the next session can pick up after an interruption.

## G0 Requirements

Don't ask what's already answered in the conversation, project docs or memory; put it straight into the requirements summary for the user to check. In the first round, ask only questions that change the route, all at once (4 at most):

1. **New or existing site?** Brand-new build / full redesign of an existing store / redesign of some pages only (e.g. product pages)
2. **Which platform?** Shopify / static HTML / WordPress + WooCommerce / Shopline, Shoplazza, etc. / other (Next.js, etc.)
3. **Selling where?** Target markets, languages, currencies (these drive the cross-border modules: multi-currency, duties, shipping, privacy law)
4. **Category and size?** What's sold, roughly how many SKUs, price range

Then collect route-specific information (as one checklist the user fills in, not one question at a time).

**New site**
- Brand name, domain, one-line positioning, target customer
- 3 reference sites (and what they like about each) and 3 direct competitors
- Product data, ideally a spreadsheet (title, price, options / variants, inventory, main image, description, category)
- Operating rules: free-shipping threshold, returns policy, delivery times, payment methods, contact email, legal entity
- Words or claims to avoid (industry term allow-list / block-list, compliance no-go areas)

**Existing site**
- URL and how to access the admin
- What must not change: navigation, URLs, checkout, specific pages, custom code, installed apps
- Current pain points ("doesn't look premium", "low conversion", "messy on mobile") and existing data (GA4, conversion rate)
- **Run a read-only audit before changing anything**: theme / template inventory, app embeds and app blocks, tracking code (GA4 / GTM / Meta / pixel sources, any double counting), custom code, SEO settings (noindex, structured data), anything broken. Report findings as 🔴 Critical / 🟡 Should fix / 🟢 Minor. These "invisible things" are what redesigns lose most often.

**Platform prep**: on Shopify, confirm the connector and permissions first and tell the user up front which steps the API can't do and they must click themselves; on static HTML, settle hosting and the cart solution first. See `references/platforms.md`.

**G0 exit:** a requirements summary (new / existing, platform, markets, scope, what must not change, known limitations) that the user confirms.

## G1 Assets ready

Before starting, list every asset with "have it? where's the link?". Links (Google Drive, Dropbox, Figma, Shopify Files, the current site) are enough; no uploads needed.

| Asset | Required? | Notes |
|---|---|---|
| Logo | Required | SVG preferred; horizontal, square, light and dark versions |
| Brand colors | Required | HEX values; if none, extract from the logo or reference sites and have the user confirm |
| Fonts | Required | Name and license source (Google Fonts is easiest) |
| Brand guidelines / reference sites | Recommended | Use guidelines if they exist, otherwise reference-site screenshots |
| Hero visual | Required | Banner image or video; video needs a fallback poster image |
| Product images | Required | At least 3 per product: white-background main, detail, scale or lifestyle |
| Product copy | Required | For an existing site, read the current data |
| Brand story / About | Recommended | Founder, timeline, origin, craft; with sources where possible |
| Review source | Recommended | Which review app, and whether real reviews exist to quote |
| Certifications | Category-dependent | Certificate or number; no evidence, no badge on the page |
| Policy text | Required | Shipping, returns, privacy, terms; free-shipping threshold and contact email must match site-wide |
| Social links | Recommended | Instagram, YouTube, TikTok, etc. |
| Creator / KOL content | Optional | Video and article links for a reviews section on product pages |
| Term allow-list / banned words | Category-dependent | Industry standards, brand vocabulary |

Rules:
- **Don't wait for everything.** Minimum to start design directions: logo, brand colors or a reference site, 1 hero visual, 1 product with complete data. Mark everything else **[PLACEHOLDER]** and fill it before the relevant gate.
- **Don't invent missing assets**, and don't pass off unrelated stock photos as product images. Use obvious placeholder blocks.
- **Resolve contradictions in the assets immediately** (e.g. the home page says "free worldwide shipping" while the announcement bar says "free shipping over $70"). Inconsistencies like this hurt trust most after launch.

**G1 exit:** the asset list (with links and gaps) is confirmed by the user and the minimum assets are in hand.

## Site structure reference

Design directions and pilot pages follow `references/site-structure.md` (global, home, collection, product page, cart and checkout, content and trust pages, cross-border, tracking and SEO). For a redesign, what the user said must not change takes priority; use the structure reference to find gaps.

## G2 HTML design directions

Goal: let the user pick one of 2–3 clearly different directions at the lowest cost, instead of iterating on the real platform.

1. **Existing site: diagnose first.** Current-state screenshots + issue list (🔴🟡🟢), and what the redesign must solve.
2. **Site map**: page list, which template each page type uses, which pages share templates. For a redesign, include an "old → new" mapping and mark what stays the same.
3. **2–3 HTML design directions**, each a self-contained single HTML file that works on desktop and mobile:
   - They must genuinely differ, e.g. A restrained premium (generous whitespace, editorial), B conversion-led (dense, trust signals up front), C narrative (brand story and origin led).
   - Use real assets and real products (real logo, real product images, real copy). No lorem ipsum, or the user can't judge.
   - At minimum: home page from hero through the trust bar; ideally also a product page above the fold.
   - Publish as shareable pages (Artifact, etc.) so the user can view on a phone and send to partners; otherwise deliver the HTML files.
4. **A comparison table**: each direction's idea, what it suits, trade-offs.
5. Ask the user to choose: A / B / C / mix (say which parts of which version).

**G2 exit:** a chosen direction, locked into a **design spec**: colors (HEX), fonts and type scale, spacing, corner radius, button styles, card styles. Record it in the progress doc; every page from here on follows it.

## G3 Pilot pages

Build the chosen direction on the real platform, but only **one pilot per template type**:
- Home page
- 1 collection page
- 2–3 product pages: a best seller, the most complex one (many variants / long description), and an edge case (no reviews, out of stock, few images)
- 1 content page (e.g. About)
- Cart

Shopify: build in the duplicated unpublished theme and share a preview link (`?preview_theme_id=`). HTML: deploy to a staging URL.

**QA the pilots yourself before showing them** (reuse this checklist for the full QA after rollout):
- [ ] Screenshots at desktop 1440px and mobile 390px, no horizontal overflow
- [ ] No Liquid / JS errors; exactly one H1 per page
- [ ] Accessibility check (axe, WCAG 2.1 AA)
- [ ] Tracking: one product view fires exactly one `page_view` and one `view_item`
- [ ] Add to cart → cart → checkout works end to end
- [ ] Existing apps (reviews, loyalty, pop-ups, filters) all load
- [ ] Edge cases: no "0 stars" when there are no reviews; videos fall back to a poster image if blocked or unplayable

Show the user: preview link + key screenshots + what changed + open decisions. Then **stop and wait for feedback**, iterate until the user is satisfied.

## G4 Sign-off

Once the pilots are approved, run a separate sign-off covering not just the look but the rollout plan:
- Complete list and count of templates and pages to change
- What each page type gets, and what stays unchanged
- Where the backups are and how to roll back
- What the user must do themselves (publish the theme, enable app embeds, paste pixel code, etc.)
- Number of batches and batch size

Move on only when the user explicitly says "start the rollout".

## Batch rollout

1. **Back up**: export all data that will change; duplicate the Shopify theme first.
2. **Run in batches**: 20–50 items per batch, logging what changed in each.
3. **Verify item by item**: read everything back from the system and compare to the target programmatically (not by eyeballing samples). Done means the counts match.
4. **Exceptions list**: anything you couldn't handle or weren't sure about goes on a separate list. Don't force it.
5. **Full QA**: rerun the G3 checklist across every template.
6. **Live QA** (after the user publishes): every page type returns 200, no errors, no duplicate tracking events, mobile add-to-cart through checkout works.
7. **Handover doc**: what was done, counts, backup locations, how to edit things in the admin, the user's to-dos, open questions.

Remind the user: changes made to the live theme between duplicating it and publishing the new one will be lost on publish, so avoid editing the live theme in that window.

## Optional phase: product content migration & copy rewrite

Use when the user wants product descriptions rewritten, terminology unified or product page content reorganized. It runs through the same gates alongside the page design: "set the standard" happens around G1, the 3 pilot products are the G3 pilot product pages, and the batch rewrite runs with the rollout after G4. Full method in `references/content-rewrite.md`.

## Gate report format

Keep it short:
- What this step completed (with counts)
- Links (preview, Artifact, docs)
- Decisions needed from the user (with options)
- What's next, starting once confirmed

## Rules

- **No gate passes without explicit user approval.** After a pilot or sample, stop and wait before going to batch.
- **Never publish or change the live site.** Publishing themes, launching the site and enabling app embeds are the user's job.
- **Never type passwords.** When the admin needs a login, the user logs in in the browser.
- **Never invent** reviews, certifications, numbers, endorsements or stories; mark gaps **[TO BE SUPPLIED BY USER]**.
- **Back up before, read back after.** Trust what you read back from the system, not the API response.
- **Out-of-scope issues go on a list** for the user to decide.

## Reference files

Read when needed:
- `references/site-structure.md` — e-commerce site structure: global, home, collection, product page, cart, content pages, cross-border, tracking and SEO
- `references/platforms.md` — prep for Shopify, static HTML, WordPress and others; what the Shopify API can't do; Shopify working notes
- `references/content-rewrite.md` — product copy rewrite: set the standard, pilot, batch with read-back, structuring product page content

## Running outside Claude

This procedure was written for Claude, and a few places name Claude tools. In ChatGPT, Codex or another agent:
- "AskUserQuestion": list numbered options in chat and let the user reply.
- "Artifact": use the platform's Canvas or equivalent; otherwise deliver self-contained HTML files.
- Connectors / MCP: use whatever tools or Actions the platform has connected; otherwise use a browser (the user logs in) or file export / import, and say which steps the user must do by hand.
- "Project" and memory: hand the progress doc to the user as a file and ask them to paste it back at the start of the next session.
