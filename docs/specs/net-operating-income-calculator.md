# Spec — Net Operating Income (NOI) Calculator

Slug: `net-operating-income-calculator` · Benchmark: landlordstudio.com NOI calculator (one rent
field + lump expenses). We win with: itemized income & expense builder, monthly/annual toggle per
line, clear "what's excluded" education, expense ratio benchmark, cap-rate tie-in.

## Inputs
**Income (itemized, add/remove rows; per-row monthly/annual toggle)**
- Base rent (default 2,200/mo), Other income rows (parking, laundry, storage, pet rent, late fees…
  preset add buttons + custom label)
- Vacancy & credit loss (% of gross income, default 5)

**Operating expenses (itemized rows with presets)**
- Property tax (3,000/yr), Insurance (1,500/yr), Property management (% of EGI or $),
  Repairs & maintenance, Utilities, Landscaping/snow, Pest control, Trash, Legal/accounting,
  Advertising, Other (custom rows)
- Prominent "Not operating expenses" info card: mortgage payments, capex, depreciation,
  income taxes — with tooltip explaining why.

## Outputs
- Hero: **NOI (annual)** + monthly equivalent.
- Potential gross income, effective gross income, total operating expenses,
  **operating expense ratio** (opex/EGI) with benchmark chip (typical 35–55%; flag if outside),
  per-unit option (optional unit count input → NOI per unit).
- Bonus: optional property value input → instant cap rate, linking to the cap rate tool.
- Bar visualization: income vs expenses vs NOI.
- Copy summary + print.
