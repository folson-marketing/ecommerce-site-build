# Platform routes

Read the section for the platform chosen at G0.

## Shopify

### Before starting

- **Confirm the Shopify connector is connected.** If not, use a connector search / suggestion tool to prompt the user to connect it; if there's no such tool, tell the user to install the Shopify connector (or MCP). State the permissions needed: read/write products, themes (`write_themes`), content (pages / blogs), files, metafields / metaobjects.
- **Tell the user up front which steps the API can't do and they must click themselves** (all learned the hard way):
  - Publishing a theme (and never write to the live MAIN theme; duplicate it as a draft first)
  - Turning app embeds on or off, and each app's own admin settings
  - Customer Events custom pixels (the agent writes the code, the user pastes it)
  - Legal policy pages (when `write_legal_policies` is missing)
  - Deleting theme files, logging in to the admin (when a browser is needed the user logs in; the agent never types passwords)
  - Filter settings in Search & Discovery

### Working notes

- Write theme files with Admin GraphQL `themeFilesUpsert`; for large files, `stagedUploadsCreate` first and reference the upload. **Only write to the duplicated draft theme.**
- For products, metafields, metaobjects and other data, go **schema → validate → execute**; use `bulkOperationRunQuery` for large exports.
- Before changing templates, list every app embed and app block, and confirm each one is still there after the migration.
- Theme styles like `.rte a` override custom components; give new components higher specificity or their own namespace.
- Site-wide facts (contact email, free-shipping threshold) appear in blogs, pages and product descriptions; when one changes, search the whole site.
- Preview link format: `https://<store-domain>/?preview_theme_id=<theme-id>`.
- Changes made to the live theme between duplicating it and publishing the new one are lost on publish; remind the user not to edit the live theme in that window.

## Static HTML / other frameworks (Next.js, etc.)

- **Hosting**: Vercel / Netlify / GitHub Pages / own server; where the repo lives. Changes go to a staging / preview URL first; production deploys need the user's approval.
- **Cart and checkout**: a static site has no cart. Choose Shopify Buy Button / Stripe Payment Links / Snipcart, etc. This shapes the page design, so settle it at G0.
- **Forms, newsletter, analytics**: which services (Formspree, Klaviyo, Mailchimp, GA4, etc.); confirm at G0.

## WordPress / WooCommerce

- Use a child theme and a staging site; never edit production directly.
- Back up the database and `wp-content` before changes; test plugin updates on staging first.

## Shopline, Shoplazza and other SaaS platforms

- Check whether the platform has an open API / MCP, and whether themes can be duplicated as previewable drafts.
- Where there's no API, use the browser (the user logs in) or the admin's bulk CSV import, still following "back up first, read back after".
- As with Shopify, list up front which steps only the user can do in the admin.
