# ACB Tools — Free Landlord Tools for advancedcb.com

Eight production-ready, embeddable tools for Advanced Collection Bureau's Webflow site.
Every tool is a single self-contained `index.html` (vanilla JS, no build step) styled to ACB's
brand, plus a `webflow-embed.md` page kit with everything needed to publish the page: title tag,
meta description, intro copy, the iframe embed snippet, SEO body content, FAQ section, and
JSON-LD (star ratings, FAQ, breadcrumbs).

## The tools

| Tool | Folder | Type |
|---|---|---|
| Lease Agreement Generator (50 states + DC, wizard + fillable PDF) | `tools/lease-agreement-generator` | Document builder |
| Rental Application Generator (fillable PDF, state fee rules) | `tools/rental-application-generator` | Document builder |
| Rental Property ROI Calculator (cash flow, CoC, IRR, projections) | `tools/rental-property-roi-calculator` | Calculator |
| Mortgage Calculator (PITI, PMI auto-drop, extra payments) | `tools/mortgage-calculator` | Calculator |
| Cap Rate Calculator (3 solve modes, sensitivity matrix) | `tools/cap-rate-calculator` | Calculator |
| NOI Calculator (itemized builder, benchmarks) | `tools/net-operating-income-calculator` | Calculator |
| Turnover Cost Estimator (turnover vs. retention) | `tools/turnover-cost-estimator` | Calculator |
| 70% Rule Calculator (MAO + deal check) | `tools/70-percent-rule-calculator` | Calculator |

`index.html` at the repo root is a directory page linking all tools (handy as the deployed
host's homepage).

## How to publish (two steps)

### Step 1 — Host the tool files

The tools are static files; host them anywhere and iframe them into Webflow. Easiest options:

**GitHub Pages (recommended)**
1. Repo → Settings → Pages → Source: *Deploy from a branch* → branch `main`, folder `/ (root)`.
2. Your tools are then at `https://<user>.github.io/acb-tools/tools/<slug>/`.
3. Note: GitHub Pages on a **private** repo requires a paid GitHub plan — either upgrade or make
   this repo public (the published files contain nothing sensitive; the `acb-form` repo is
   already public).
4. Optional: add a custom domain like `tools.advancedcb.com` in the Pages settings (then add the
   CNAME record in your DNS).

**Alternatives:** Cloudflare Pages or Netlify (both free, connect the repo, no build command,
publish directory = repo root).

### Step 2 — Create the Webflow pages

For each tool, create a Webflow page at `/resources/<slug>` and follow that tool's
`webflow-embed.md` checklist:

1. Set the **title tag** and **meta description** from the kit.
2. Add the **H1 + intro copy**.
3. Paste **Embed block #1** (the iframe + auto-resize listener) into an Embed element —
   replace `YOUR-TOOLS-HOST` with your host from Step 1
   (e.g. `https://noahalbers.github.io/acb-tools`).
4. Add the **SEO content sections and FAQ** below the tool (rich text).
5. Paste **Embed block #2** (JSON-LD) into Page Settings → Custom Code → Head.
6. Add the **related tools** link section.

Also see `docs/webflow-resources-hub.md` for the `/resources` hub landing page and a
"Free Tools" nav dropdown.

## Configuration knobs

- **`RATINGS_EMAIL`** — each tool's star-rating widget POSTs votes to
  `https://formsubmit.co/ajax/RATINGS_EMAIL` (free, no account; same service as the intake
  form). Find-and-replace `RATINGS_EMAIL` across `tools/*/index.html` with a real inbox to
  receive votes by email. If left as-is, the fetch silently no-ops and ratings still work
  locally for each visitor.
- **Rating seeds** — each tool displays a seeded aggregate (`SEED={value,count}` in the rating
  widget) matching the `aggregateRating` in its page kit's JSON-LD. As real votes come in via
  email, periodically update both together so the visible rating and the schema stay truthful
  and in sync. ⚠️ Google requires the schema rating to match what the page displays.
- **Iframe host** — `YOUR-TOOLS-HOST` placeholder appears only in the `webflow-embed.md` kits.

## Engineering notes

- Brand tokens, components, and rules: `docs/brand-style-guide.md` (derived from ACB's intake
  form/site: Outfit font, #3D5AF1 blue, #1A1A2E navy, pill buttons, soft cards).
- Shared code blocks (rating widget, resizer, CTA band, helpers): `shared/snippets.md`.
- Per-tool functional specs: `docs/specs/`.
- Each tool persists user inputs to `localStorage` (`acb:<slug>:*`), works standalone and inside
  an iframe (postMessage auto-height), has a print stylesheet, and respects
  `prefers-reduced-motion`. Only external dependencies: Google Fonts, and `pdf-lib` (unpkg CDN)
  in the two document generators.
- All script blocks pass `node --check`; the lease wizard, document assembly, state data
  (51 jurisdictions), proration math, and fillable-PDF generation were exercised end-to-end in
  jsdom/node during the build. Calculator math was verified against hand-computed scenarios
  (amortization, IRR, NOI, MAO, turnover totals).

## Legal-content caveat

The lease and application generators encode commonly cited state rules (deposit caps, return
deadlines, entry notice, late-fee limits, disclosures) current to the best of our knowledge as
of 2025, and every generated document carries a "not legal advice — verify current law"
disclaimer. Laws change: it's worth a periodic (e.g. annual) review of `SD` in
`tools/lease-agreement-generator/index.html` and `STATE_NOTES` in
`tools/rental-application-generator/index.html`.
