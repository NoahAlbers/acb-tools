# Navbar: Resources mega menu plan

The current Resources dropdown (4 feature rows + "Additional Resources" footer) tops out around
6–7 items. With 15+ tools, the move is a **two-column mega menu** — exactly the Monogram-style
layout from your screenshots, which also stays visually consistent with your existing dropdown
(icon tile + colored title + one-line description, white card, soft shadow).

## Recommended structure

```
┌────────────────────────────────────────────────────────────────────┐
│  DOCUMENTS & NOTICES              CALCULATORS                      │
│  (feature rows, icon+desc)        (compact 2-col grid, icon+title) │
│                                                                    │
│  📄 Lease Agreement Generator      🧮 Rental Property ROI           │
│     Build a state-specific...      🏠 Mortgage                      │
│  📋 Rental Application             ％ Cap Rate                      │
│     Fair-housing-safe...           💵 Net Operating Income          │
│  ✉️ Late Rent Notice               🔄 Turnover Cost                 │
│     Pay-or-quit with your...       🧾 70% Rule                      │
│  🛡 Deposit Return Letter          📅 Prorated Rent                 │
│     Itemized, deadline-aware...    📈 Rent Increase                 │
│  📈 Rent Increase Notice           🛡 Deposit Interest              │
│     State notice rules...                                          │
│  🏠 Move-In/Move-Out Checklist                                     │
│     Room-by-room with photos...                                    │
│────────────────────────────────────────────────────────────────────│
│  Additional: Eviction Notice Template · Rental Yield · Client      │
│  Resources                      →  View all free tools             │
└────────────────────────────────────────────────────────────────────┘
```

Why this split: the six documents are the high-intent items and deserve descriptions; the nine
calculators are self-explanatory from their names, so a compact title-only grid keeps the menu
scannable instead of a wall of text. The footer bar keeps your existing "Additional Resources"
pattern and adds **"View all free tools →" linking to `/resources`** (the searchable hub page) —
that's the escape hatch so the menu never has to be exhaustive.

On mobile, Webflow's nav collapses the dropdown — keep just the two column headers as
accordion groups, or simply link "Free Tools" straight to `/resources` and let the hub's
search do the work (recommended: simplest and the hub is built for it).

## Paste-ready menu copy (matches your existing description voice)

**Documents & Notices** (feature rows):
| Title | Description |
|---|---|
| Lease Agreement Generator | Build a state-specific lease in minutes, free. |
| Rental Application Generator | A fair-housing-safe application with fillable PDF. |
| Late Rent Notice | Pay-or-quit notices with your state's deadline computed. |
| Security Deposit Return Letter | Itemized, deadline-aware deposit letters. |
| Rent Increase Notice | State notice rules and rent-control caps handled. |
| Move-In / Move-Out Checklist | Room-by-room inspections with photos and PDF reports. |

**Calculators** (compact grid, titles only — tooltips optional):
Rental Property ROI · Mortgage · Cap Rate · Net Operating Income · Turnover Cost ·
70% Rule · Prorated Rent · Rent Increase · Security Deposit Interest

**Footer bar:** Eviction Notice Template · Advanced Rental Yield Calculator · Client Resources
· **View all free tools →** (`/resources`)

## Cloneables to start from

These are free, community-vetted starting points in exactly this pattern (clone, restyle to
your tokens, swap the copy above in):

- [Webflow Mega Navigation by Flowbase](https://www.flowbase.co/clone/webflow-mega-navigation) —
  clean classes, native Webflow interactions, mobile version included; closest to the
  two-column layout above.
- [5 Mega Menus cloneable by BRIX Templates](https://brixtemplates.com/cloneables/5-megamenus-webflow-cloneable-template) —
  five variants in one clone; variant with "feature column + link grid" matches the plan.
- [Mega Menu Dropdown Navigation (FlowRadar)](https://www.flowradar.com/cloneables/mega-menu-dropdown-navigation)
  and the broader [FlowRadar menu category](https://www.flowradar.com/cloneable-categories/menu)
  (55 menu cloneables) for hover-trigger versions.
- Browse-more pools: [Made in Webflow: mega menu](https://webflow.com/made-in-webflow/mega-menu)
  and [meganavigation](https://webflow.com/made-in-webflow/meganavigation).

Implementation notes for whichever you clone:
1. Copy the cloned dropdown into your existing Navbar symbol so the trigger ("Resources ▾")
   and positioning stay consistent with the Services dropdown.
2. Reuse your existing icon-tile component (the pastel rounded squares) for the document rows —
   the visual continuity with Services matters more than the cloneable's own icons.
3. Set the dropdown list's width to the navbar container (or ~900px centered) rather than
   full-bleed; your current dropdowns are card-style, not full-width bars.
4. Keep dropdown links as plain `<a>` to `/resources/<slug>` — no JS needed.
