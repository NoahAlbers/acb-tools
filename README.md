# ACB Tools — Free Landlord Tools for advancedcb.com

Eleven production-ready, embeddable tools for Advanced Collection Bureau's Webflow site.
Every tool is a single self-contained `index.html` (vanilla JS, no build step) styled to ACB's
brand, plus a `webflow-embed.md` page kit with everything needed to publish the page: title tag,
meta description, intro copy, the iframe embed snippet, SEO body content, FAQ section, and
JSON-LD (star ratings, FAQ, breadcrumbs).

## The tools

| Tool | Folder | Type |
|---|---|---|
| Lease Agreement Generator (50 states + DC, wizard, clause presets, fillable PDF) | `tools/lease-agreement-generator` | Document builder |
| Rental Application Generator (fillable PDF, state fee rules) | `tools/rental-application-generator` | Document builder |
| Late Rent Notice Generator (friendly reminder / pay-or-quit, state cure periods + computed deadlines) | `tools/late-rent-notice-generator` | Notice generator |
| Security Deposit Return Letter (state deadlines, itemized deductions, balance-owed mode) | `tools/security-deposit-return-letter-generator` | Notice generator |
| Rent Increase Notice Generator (state notice periods, rent-control warnings, effective-date validation) | `tools/rent-increase-notice-generator` | Notice generator |
| Rental Property ROI Calculator (cash flow, CoC, IRR, save & compare scenarios, stress test) | `tools/rental-property-roi-calculator` | Calculator |
| Mortgage Calculator (PITI, PMI auto-drop, extra payments, rate-shopping table) | `tools/mortgage-calculator` | Calculator |
| Cap Rate Calculator (3 solve modes, sensitivity matrix) | `tools/cap-rate-calculator` | Calculator |
| NOI Calculator (itemized builder, benchmarks, CSV export) | `tools/net-operating-income-calculator` | Calculator |
| Turnover Cost Estimator (turnover vs. retention, portfolio mode) | `tools/turnover-cost-estimator` | Calculator |
| 70% Rule Calculator (MAO + deal check) | `tools/70-percent-rule-calculator` | Calculator |

**Shareable scenario links:** every calculator encodes its inputs in a `#acb=` URL fragment with
a "Copy link to this scenario" button. The embed snippets forward the Webflow page's hash into
the iframe, so shared links open the tool pre-filled on advancedcb.com. (Document/notice tools
intentionally skip this — they contain personal names.) See `docs/competitive-analysis.md` for
the persona analysis behind the v2 feature set.

`index.html` at the repo root is a directory page linking all tools (handy as the deployed
host's homepage).

## How to publish (two steps)

### Step 1 — GitHub Pages hosting (same setup as `acb-form`)

The tools are static files served straight from this repo via GitHub Pages. Every embed snippet
in the `webflow-embed.md` kits already points at the live host:
`https://noahalbers.github.io/acb-tools/tools/<slug>/`

To turn it on (one time):

1. **Merge this branch into `main`** (the tools were built on
   `claude/advanced-cb-tools-xoi2la`).
2. **Make the repo public** — GitHub Pages on a private repo requires a paid plan. The
   published files contain nothing sensitive, and `acb-form` is already public.
3. **Settings → Pages → Build and deployment → Source: “Deploy from a branch” →
   branch `main`, folder `/ (root)` → Save.** The site goes live a minute later.

Sanity checks once enabled:
- `https://noahalbers.github.io/acb-tools/` → the tools directory page
- `https://noahalbers.github.io/acb-tools/tools/cap-rate-calculator/` → a working calculator

(A `.nojekyll` file is included so Pages serves files as-is.) Optional later: add a custom
domain like `tools.advancedcb.com` in the same Pages settings screen and update the kit URLs.
Pushes to `main` redeploy automatically — that's the whole pipeline.

### Step 2 — Create the Webflow pages

For each tool, create a Webflow page at `/resources/<slug>` and follow that tool's
`webflow-embed.md` checklist:

1. Set the **title tag** and **meta description** from the kit.
2. Add the **H1 + intro copy**.
3. Paste **Embed block #1** (the iframe + auto-resize listener) into an Embed element —
   it already points at the GitHub Pages host.
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
- **Iframe host** — hard-coded to `https://noahalbers.github.io/acb-tools` in the
  `webflow-embed.md` kits; change there if you later move to a custom domain.

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

The document and notice generators encode commonly cited state rules (deposit caps, return
deadlines, entry notice, late-fee limits, disclosures, nonpayment cure periods, rent-increase
notice periods) current to the best of our knowledge as of 2025, and every generated document
carries a "not legal advice — verify current law" disclaimer. Laws change: it's worth a periodic
(e.g. annual) review of `SD` in `tools/lease-agreement-generator/index.html`, `STATE_NOTES` in
`tools/rental-application-generator/index.html`, `CURE` in
`tools/late-rent-notice-generator/index.html`, `DEP` in
`tools/security-deposit-return-letter-generator/index.html`, and the notice data in
`tools/rent-increase-notice-generator/index.html`.
