# Spec — Rental Turnover Cost Estimator

Slug: `turnover-cost-estimator` · Benchmark: blog.narrpr.com/turnover (article, no real tool).
There is no great interactive turnover calculator out there — we can own this query. 

## Inputs (itemized, all editable, grouped; checkboxes to include/exclude line items)
**Vacancy**
- Monthly rent ($, default 2,200)
- Expected days vacant (slider 0–120, default 30) → lost rent auto = rent/30.44 × days
- Utilities + lawn/snow during vacancy ($/mo, default 150)

**Make-ready**
- Cleaning (default 300), Painting (default 900), Carpet/flooring (default 500),
  Repairs & maintenance (default 600), Locks/rekey (default 75), Landscaping touch-up (default 0),
  Appliance replacement (default 0)

**Leasing**
- Advertising/listing (default 100)
- Leasing fee / placement (choose % of one month's rent [default 50%] or flat $)
- Tenant screening cost not recovered (default 0)
- Concessions (free rent/discounts, default 0)

**Admin & loss**
- Unpaid rent / damages beyond deposit ($, default 0) → when > 0, show inline ACB callout:
  "Former tenant owes you money? That's exactly what we collect."
- Eviction/legal costs (default 0)

## Outputs
- Hero: **Total turnover cost** + "= X.X months of rent" equivalence chip.
- Donut by category (vacancy, make-ready, leasing, admin/loss).
- **Retention comparison card**: side-by-side — cost of turnover vs cost of retaining
  (user-set renewal incentive, default $200, + skipping a rent increase option) →
  "Keeping a good tenant saves you $X".
- Annualized view: with average tenancy length input (years, default 3) → turnover cost per year.
- Copy summary + print.
