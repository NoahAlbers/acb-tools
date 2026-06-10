# Spec — Mortgage Calculator (Investment-property aware)

Slug: `mortgage-calculator` · Benchmark: landlordstudio.com/calculators/free-mortgage-calculator
(basic). We win with: full PITI breakdown, extra-payment modeling, amortization schedule + chart,
landlord framing (rent coverage check).

## Inputs
- Home price ($, default 300,000)
- Down payment (synced % and $, default 20%)
- Interest rate (%/yr, default 7.0)
- Loan term (select 30/20/15/10, default 30)
- Start date (month/year, default next month)
- Property tax ($/yr, default 3,000)
- Home insurance ($/yr, default 1,500)
- PMI (%/yr of loan, default 0.5, auto-applied only when down <20% — show hint chip "PMI applies
  under 20% down"; drops automatically at 78% LTV in schedule)
- HOA ($/mo, default 0)
- Extra monthly payment ($, default 0) and one-time extra payment ($ + date, optional)
- Optional: expected monthly rent ($) → shows rent coverage ratio (rent vs PITI) chip.

## Outputs
- Hero: **Total monthly payment** with donut breakdown (P&I, tax, insurance, PMI, HOA).
- Loan amount, total interest paid, total cost of loan, payoff date.
- With extra payments: interest saved, time saved, new payoff date (side-by-side vs baseline).
- Amortization: SVG line chart (balance, principal paid, interest paid over time) +
  expandable schedule table (yearly rollup rows, expandable to monthly per year).
- Rent check (if rent provided): PITI vs rent, surplus/shortfall colored.

## Math
- P&I standard amortization; PMI charged monthly until balance/price ≤ 0.78.
- Extra payments applied to principal; recompute schedule iteratively.
- Edge: 0% rate, 100% down ("no loan needed").
