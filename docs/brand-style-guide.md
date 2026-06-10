# ACB Tools — Brand & Style Guide

This guide governs every tool in this repo. It is derived from Advanced Collection Bureau's
existing web properties (advancedcb.com and the ACB intake form), so tools feel native to the brand.

## Brand voice

- Professional but warm and plainspoken. We talk to landlords and property managers like peers.
- Confident, helpful, zero fluff. Short sentences. No legalese outside of generated documents.
- ACB credibility hooks (use sparingly, e.g. in the CTA): 25+ years in residential rental
  collections, $85M+ recovered for property managers and landlords.
- Every tool is **100% free, no signup, no email wall**. Say so near the top of each tool.

## Design tokens

Font: **Outfit** (Google Fonts), weights 300–800. Fallback `sans-serif`.

```css
:root {
  --acb-blue:       #3D5AF1;  /* primary */
  --acb-blue-dark:  #2D45C6;  /* hover / gradients */
  --acb-blue-light: #EEF1FE;  /* selected backgrounds, chips */
  --acb-blue-mid:   #D5DBFC;  /* borders on selected items */
  --acb-bg:         #F4F5F9;  /* page background */
  --acb-card:       #FFFFFF;  /* card background */
  --acb-text:       #1A1A2E;  /* headings / primary text */
  --acb-text-mid:   #4A4A68;  /* body text */
  --acb-text-light: #8889A0;  /* captions, hints */
  --acb-border:     #E2E4EC;  /* card & input borders */
  --acb-warn:       #E8A83E;  /* warnings */
  --acb-warn-bg:    #FEF9EE;  /* warning backgrounds */
  --acb-green:      #16A34A;  /* success / positive numbers */
  --acb-red:        #DC2626;  /* errors / negative numbers */
  --acb-gold:       #F5B301;  /* star ratings */
}
```

## Component conventions

- **Page**: `background: var(--acb-bg)`, content max-width 1080px (calculators) or 880px
  (wizards), centered, 16px side padding. `font-family:'Outfit',sans-serif`.
- **Cards**: white, `border:1px solid var(--acb-border)`, `border-radius:16px`,
  `box-shadow:0 2px 12px rgba(0,0,0,0.04)`, padding 24–28px.
- **Primary buttons**: pill (`border-radius:50px`), `background:var(--acb-blue)`, white text,
  weight 600, padding `14px 36px`, `box-shadow:0 4px 18px rgba(61,90,241,0.27)`.
  Hover: `background:var(--acb-blue-dark)`, translateY(-1px). Disabled: `#D0D3DC` bg, `#8889A0` text, no shadow.
- **Secondary buttons**: white bg, `1.5px solid var(--acb-border)`, pill, `--acb-text-mid` text.
- **Inputs**: white, `1.5px solid var(--acb-border)`, `border-radius:10px`, padding `13px 16px`,
  16px font (prevents iOS zoom). Focus: border `--acb-blue` + `box-shadow:0 0 0 3px rgba(61,90,241,0.09)`.
  Money inputs get a `$` prefix inside the field wrapper; percent inputs a `%` suffix.
- **Choice pills / segmented controls**: pill buttons; selected = `--acb-blue-light` bg,
  `1.5px solid var(--acb-blue)`, blue 600-weight text with a leading ✓ where natural.
- **Sliders**: native range inputs with `accent-color:var(--acb-blue)`, always paired with a
  synced number input (slider for feel, field for precision).
- **Section labels**: 12px, weight 700, letter-spacing .08em, uppercase, `--acb-text-light`.
- **Results emphasis**: hero numbers 32–40px weight 800; positive = `--acb-green`,
  negative = `--acb-red`, neutral = `--acb-text`.
- **Info tooltips**: small ⓘ after labels; tap/hover reveals a plain-English explanation.
  Every finance term gets one. Mobile: tap to toggle.
- **Progress bar** (wizards): 4px bar fixed to top of the tool, gradient
  `linear-gradient(90deg,var(--acb-blue),var(--acb-blue-dark))`.
- **Animation**: subtle fade/slide-in (180–400ms ease). Respect `prefers-reduced-motion`.

## Accessibility

- Semantic HTML, labels bound to inputs, `aria-live="polite"` on result regions,
  keyboard operable wizards (Enter advances when valid), focus-visible outlines,
  WCAG AA contrast (the token pairs above pass on white/`--acb-bg`).

## Required page blocks (every tool, in order)

1. **Tool header** — H1 (in Webflow page, not iframe; the iframe shows a styled tool title bar),
   one-line subtitle, "Free • No signup • No email required" badge row.
2. **The tool itself.**
3. **Star rating widget** — visible "X.X ★ | N ratings" + clickable 5-star input
   (see `shared/snippets.md`). Matches the page's `AggregateRating` JSON-LD.
4. **ACB CTA band** — see copy below.
5. **Disclaimer** — tools: "estimates, not financial advice"; documents: "not legal advice,
   review with a local attorney; laws change — verify current requirements."

## ACB CTA band (standard copy)

> **Tenant left owing money?** Advanced Collection Bureau has recovered over $85 million in
> unpaid rent, fees, and damages for landlords and property managers. No recovery, no fee.
> [Get Started →](https://www.advancedcb.com/) · or call [(321) 633-4999](tel:3216334999)

Style: `--acb-blue-light` background card, blue left border (4px), pill CTA button.

## Engineering rules

- One **self-contained** `index.html` per tool: inline CSS + vanilla JS. No frameworks, no build.
  Allowed CDN deps: Google Fonts; `pdf-lib` (unpkg) only in the document generators.
- Tools must work standalone **and** inside an iframe (auto-height postMessage resizer —
  exact snippet in `shared/snippets.md`).
- All money via `Intl.NumberFormat('en-US',{style:'currency',currency:'USD'})`; round display
  to whole dollars unless cents matter (mortgage payments).
- Inputs persist to `localStorage` (namespaced `acb:<tool-slug>:*`) so users don't lose work.
- Recompute live on input — no "Calculate" gate for calculators (still show a clear primary
  action where a wizard step needs one).
- Charts: inline SVG/canvas helpers only, no chart libraries.
- Print stylesheet on every tool; document generators must produce clean paginated print output
  (that's the "Save as PDF" path) plus a pdf-lib fillable blank template.
- Mobile-first: single column under 720px, tap targets ≥44px.
- No external analytics, no tracking, no data leaves the page (ratings POST is the one
  documented exception and is fire-and-forget).
