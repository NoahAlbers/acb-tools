# Spec — Rental Property ROI Calculator

Slug: `rental-property-roi-calculator` · Benchmark to beat: calculator.net/rental-property-calculator.html
(comprehensive but ugly, dense, no guidance). We win on: clean grouped inputs with plain-English
tooltips, live results, charts, year-by-year table, IRR done right, mobile usability.

## Inputs (grouped cards; all live-update; sensible defaults shown)

**Purchase**
- Purchase price ($, default 250,000)
- Use loan? (toggle, default yes)
- Down payment (% with synced $ display, default 20%)
- Interest rate (%/yr, default 7.0)
- Loan term (years, default 30)
- Closing costs ($, default 6,000)
- Repairs/rehab up front ($, default 0); After-repair value ($, optional — defaults to purchase price + repairs)

**Income**
- Monthly rent ($, default 2,200)
- Other monthly income ($ — parking, storage, laundry; default 0)
- Vacancy rate (%, default 5)
- Annual rent growth (%, default 3)

**Operating expenses**
- Property tax ($/yr, default 3,000) + annual increase % (default 3)
- Insurance ($/yr, default 1,500) + annual increase %
- HOA ($/mo, default 0)
- Maintenance/repairs (% of rent, default 8)
- CapEx reserve (% of rent, default 5)
- Property management (% of collected rent, default 0 — "self-managing?" hint)
- Utilities paid by owner ($/mo, default 0)
- Other ($/yr, default 0)
- Other expenses annual increase % (default 3, applies to HOA/utilities/other)

**Sale / exit**
- Hold length (years slider 1–30, default 10)
- Annual appreciation (%, default 3)
- Selling costs (% of sale price, default 7)

## Outputs

Hero strip (first year): **Monthly cash flow**, **Cash-on-cash return**, **Cap rate (on purchase)**, **NOI (yr 1)**.
Secondary: total cash invested, loan amount, monthly P&I, GRM, DSCR, break-even ratio,
operating expense ratio, 1% rule check (rent ÷ price, pass/fail chip).

**At sale (hold horizon):** projected sale price, loan balance, sale proceeds after costs,
total profit when sold (proceeds + cumulative cash flow − cash invested), **annualized return (IRR)**
on all cash flows including sale, and total return multiple.

**Charts (inline SVG):**
1. Donut: where the monthly rent goes (P&I, taxes, insurance, maintenance+capex, management, other, cash flow).
2. Stacked area/line over hold period: equity (from amortization + appreciation) vs cumulative cash flow.

**Year-by-year table** (toggleable, print-friendly): year, gross rent, vacancy, operating expenses,
NOI, debt service, cash flow, cumulative cash flow, property value, loan balance, equity,
total return if sold that year + IRR if sold that year.

## Math notes

- Monthly P&I: `P*r/(1-(1+r)^-n)`, r = rate/12. Handle 0% and cash purchase (no loan rows).
- Effective gross income yr t: `(rent*12 + other*12) * (1+rentGrowth)^(t-1) * (1-vacancy)`.
- % -of-rent expenses scale with rent growth; fixed expenses grow at their own rate.
- IRR: Newton/bisection on monthly... yearly cash flows is fine: CF0 = −(down + closing + repairs),
  CFt = annual cash flow, final year adds net sale proceeds. Bisection between −99% and 100%.
- Cap rate = NOI yr1 / purchase price (note in tooltip: some use price + repairs; we show both
  purchase-basis and all-in-basis in tooltip text).
- DSCR = NOI / annual debt service.

## Extras

- "Copy results summary" button (plain-text summary to clipboard).
- Print stylesheet: inputs collapse to a summary, table prints fully.
- Edge cases: rent 0, 100% down, 0 years hold (min 1), negative cash flow shown red with a
  gentle callout ("This property loses money each month at these assumptions").
