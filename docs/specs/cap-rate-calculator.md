# Spec — Cap Rate Calculator

Slug: `cap-rate-calculator` · Benchmark: mynd.co/cap-rate-calculator (clean but shallow, lead-gen
gated). We win with: three solve modes, NOI builder built in, sensitivity matrix, plain-English
education, no gating.

## Modes (segmented control)
1. **Solve cap rate** — inputs: property value/price, NOI (either direct $ or "help me calculate"
   expander with mini income/expense builder: rent, other income, vacancy %, itemized or
   % -based expenses). Output hero: cap rate %.
2. **Solve max price** — inputs: NOI + target cap rate → max purchase price.
3. **Solve required NOI** — inputs: price + target cap rate → NOI needed (+ monthly rent hint
   at a given expense ratio).

## Outputs
- Hero number + interpretation chip: <4% "Low — typical for Class A / low-risk",
  4–7% "Moderate — typical buy-and-hold range", 7–10% "High — value/risk tradeoff",
  >10% "Very high — verify numbers & risk".
- Sensitivity matrix table: cap rate across price ±10% (5 steps) × NOI ±10% (5 steps),
  current cell highlighted.
- "Cap rate vs cash-on-cash" explainer card (cap rate ignores financing) with link to ROI calculator.
- Education content for the Webflow kit: what's a good cap rate, cap rate vs cash on cash,
  why cap rate excludes mortgage, NOI definition.
