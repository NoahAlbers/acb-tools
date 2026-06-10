# Spec — 70% Rule Calculator (Fix & Flip Max Offer)

Slug: `70-percent-rule-calculator` · Benchmark: landlordstudio.com 70% calculator (single formula,
no context). We win with: adjustable rule %, full deal-check breakdown, reverse mode, profit waterfall.

## Inputs
- After Repair Value (ARV $, default 300,000) with tooltip on how to estimate (comps)
- Estimated repair costs ($, default 40,000)
- Rule percentage (slider 60–85%, default 70, with chips: "65% — expensive markets/high risk",
  "70% — standard", "75–80% — competitive markets/wholetail")

## Outputs
- Hero: **Maximum Allowable Offer (MAO)** = ARV × rule% − repairs.
- Breakdown bar (waterfall): ARV → minus 30% margin (holding/closing/profit) → minus repairs → MAO.
- "Where the 30% goes" education card: typical buy/hold/sell costs (~10–15%) + target profit (~15–20%).
- **Deal check mode** (second tab): enter an actual asking/offer price → shows implied margin %,
  projected gross profit at ARV, and verdict chip (Good deal / Thin / Over MAO).
- Reverse: given offer price + repairs → break-even ARV needed.
- Sensitivity table: MAO across ARV ±10% × repairs ±25%.
