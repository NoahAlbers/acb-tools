# Spec — Rent Increase Notice Generator

Slug: `rent-increase-notice-generator` · Rating seed {value:4.8,count:189}
Annual recurring need; rent-control states make landlords nervous — we validate the notice
period and warn about caps. Builder + live preview (structural exemplar:
`tools/rental-application-generator/index.html`).

## State data
Base notice period: copy the `mtm` month-to-month values verbatim from `SD` in
`tools/lease-agreement-generator/index.html` (the conservative default — terminating and
changing terms generally use the same notice). Then apply these **overrides/extras** in an
`INC` object; entries get cap warnings where noted. Global "verify — local rent control may
add rules" hedge, and a city flag list (NYC, San Francisco, LA, St. Paul, Newark/Jersey City,
Portland OR, Seattle, Washington D.C., Montgomery Co. MD) that triggers an extra "this city has
its own rent rules" warning chip when the typed city matches.

- CA: 30 days if total increases ≤10% in 12 months; **90 days if >10%**. AB 1482 caps increases
  at 5% + regional CPI (10% absolute max) for most buildings 15+ years old.
- OR: 90 days' notice; statewide cap (7% + CPI, 10% max for buildings over 15 years; no cap
  first year of occupancy rules — verify current figure).
- WA: recent statewide law caps most increases (roughly 7% + inflation, 10% max) and extended
  notice requirements (60–90 days) — verify current statute.
- CO: 60 days; increases limited to once per 12 months.
- NY: depends on occupancy length for increases ≥5%: 30 days (<1 yr), 60 days (1–2 yrs),
  90 days (2+ yrs). Rent-stabilized units follow RGB orders instead.
- NJ: one full month; many municipalities have local rent control with their own caps.
- DC: rent-stabilized units capped (CPI-based) with registration requirements.
- DE: 60 days. · ME: 45 days (75 days for increases of 10%+ — verify; Portland ME has rent
  control). · MD: 60 days in several counties; local rules vary. · MN: statewide no cap;
  St. Paul has rent stabilization. · VT: 60 days. · AZ: 30 days. · FL: no statewide notice
  statute for fixed-term expiry; month-to-month follows termination notice (30 days).

## Builder
1. **State + city** → rules panel (notice period, caps if any, computed **earliest effective
   date**).
2. **Parties & property**: landlord, tenant(s), address.
3. **The increase**: current rent $, new rent $ → live chips: increase $, increase %, new
   annualized cost. **Cap warning** when % exceeds a capped state's threshold (CA >10% triggers
   90-day + cap warning; OR/WA over ~10% warning; CO frequency reminder).
4. **Dates**: notice delivery date (default today) + tenancy type (month-to-month / fixed-term
   renewal). Effective date input with validation: must be ≥ delivery + notice period AND
   (for month-to-month) aligned to a rental-period start (1st of month if rent due the 1st —
   compute and suggest the earliest valid 1st). Fixed-term mode: effective at renewal; offer
   renewal-with-new-rate language.
5. **Tone options**: optional appreciation line (default on: "We value you as a resident…"),
   optional reason line (select: market adjustment / increased taxes & insurance / property
   improvements / custom), optional "please reply by" date for renewal decisions.

## Document output
Professional notice letter: current rent, new rent, effective date, the notice-period sentence
citing the state minimum, what happens next (for m2m: tenancy continues at new rate; tenant may
give notice per lease if declining), signature block, certificate of service optional.
Print/save-PDF + copy. Disclaimers (not legal advice; rent control varies by city; verify).
Builder education card: retention math — "A $50 increase that causes a turnover costs you more —
check the Turnover Cost Estimator" (link /resources/turnover-cost-estimator).
ACB CTA standard copy.
