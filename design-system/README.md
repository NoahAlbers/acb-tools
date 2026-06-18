# Advanced Collection Bureau, Design System

A reusable design language distilled from advancedcb.com and the free landlord tools.
Hand this folder (or just `tokens.css`) to anyone, or to Claude, and ask them to build
"in the ACB style."

- **`index.html`** is the living style guide. Open it in a browser to see every token,
  component, and pattern rendered. Click a color swatch to copy its hex.
- **`tokens.css`** is the source of truth: CSS custom properties for color, type, radius,
  elevation, and spacing. Reference variables, never raw hex.
- The deeper brand and engineering rules (per-tool page blocks, accessibility, build
  constraints) live in `../docs/brand-style-guide.md`.

## The feel in one line

Confident dark navy heros, a single bright cobalt accent, soft rounded white cards, and
clean Outfit type. Calm neutrals, one strong action color, generous corners.

## Foundations

- **Type:** Outfit (Google Fonts), 300 to 800. Headings heavy and tight (800, negative
  tracking). Body 16px in muted navy (`--acb-text-mid`). Stats and key numbers are 800 in
  cobalt. Section labels are 12px, 700, uppercase, 0.10em tracking, in `--acb-text-light`.
- **Color:** one cobalt (`--acb-blue #3D5AF1`) carries all action and emphasis. Type is a
  near-black navy (`--acb-text #1A1A2E`). Surfaces are white on a faint lavender-gray page
  (`--acb-bg #F4F5F9`). Dark sections use `--acb-dark #24243A`. Green/red only for
  positive/negative results; gold only for stars.
- **Radius:** 8px inputs, 12px inner panels, 16px cards, 50px (pill) buttons and badges.
- **Elevation:** `--acb-shadow-card` at rest, `--acb-shadow-raise` for images and popovers,
  `--acb-shadow-blue` (a cobalt glow) on primary buttons.
- **Spacing:** 4px base scale (4, 8, 12, 16, 20, 24, 32, 40, 56, 72).
- **Motion:** subtle fade and slide, 180 to 400ms, always respecting `prefers-reduced-motion`.

## Core components

- **Primary button:** cobalt pill, white text, weight 600, cobalt glow. Hover darkens and
  lifts 1px. Disabled goes gray, no shadow.
- **Secondary button:** white pill, 1.5px neutral border, muted text.
- **Link with arrow:** bold cobalt label with a trailing arrow that nudges right on hover.
- **Card:** white, 1px border, 16px radius, soft card shadow, 24 to 28px padding. Optional
  44px tinted icon tile (`--acb-blue-light` bg, cobalt glyph).
- **Badge / chip:** pill, `--acb-blue-light` bg with cobalt text (or white with a border).
- **Form field:** white input, 1.5px border, 8px radius, 16px font (prevents iOS zoom).
  Focus adds a cobalt ring. Money gets a `$` prefix, rates a `%` suffix. Sliders pair with a
  synced number field and use `accent-color: var(--acb-blue)`.
- **Choice pills / segmented control:** pills that tint `--acb-blue-light` with a cobalt
  border and text when selected.
- **Info tooltip:** a small ⓘ after a label; hover or tap reveals a plain-English bubble.
- **Result number:** weight 800; positive green, negative red, neutral navy.
- **Star rating:** gold stars over a visible aggregate, one vote per browser.

## Signature patterns

- **Dark hero:** navy surface, white heading (optional cobalt gradient on a key word), muted
  gray subhead, one cobalt pill action.
- **Feature checklist + framed image:** a square photo with two offset decorative squares
  (one `--acb-blue`, one `--acb-blue-deep`), beside a cobalt-checkmark list.
- **Stat block:** 2 or 4 big cobalt numbers (weight 800) with small gray labels.
- **CTA band:** `--acb-blue-light` panel with a 4px cobalt left border and a pill action.

## Voice

Professional but warm and plainspoken; short, confident sentences; zero fluff. Lead with
free, no signup, no email. Credibility hooks (25+ years, $85M+ recovered) used sparingly,
usually in the CTA. No legalese outside generated documents.

**Writing rule:** never use em dashes or en dashes in copy. Use commas, "to" for ranges
(5% to 8%), or a middot. This applies everywhere a reader sees text.

Standard disclaimers: calculators say estimates only, not financial advice; document
generators say not legal advice, review with a local attorney, laws change so verify
current requirements.
