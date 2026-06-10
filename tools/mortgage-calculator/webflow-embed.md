# Webflow page kit — Mortgage Calculator

Target URL: `https://www.advancedcb.com/resources/mortgage-calculator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Mortgage Calculator for Rental Property — Free Investment Property Mortgage Calculator | Advanced Collection Bureau
- **Meta description:** Free mortgage calculator for rental property investors. Full PITI breakdown, PMI that drops automatically, extra-payment savings, amortization schedule, and a rent-coverage check. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Mortgage Calculator for Rental Property
2. Intro paragraph (below H1):
   > Estimate the true monthly payment on an investment property — principal, interest, taxes, insurance, PMI, and HOA — then see how extra payments shorten the loan and whether the rent actually covers the bill. Free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Mortgage Calculator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/mortgage-calculator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='mortgage-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: How mortgage payments are calculated (PITI)
A mortgage payment has four standard parts — **P**rincipal, **I**nterest, **T**axes, and **I**nsurance, or PITI. Principal and interest come from the amortization formula: each month you pay interest on the remaining balance (annual rate ÷ 12 × balance), and the rest of the fixed payment reduces principal. Early on, most of the payment is interest; the split flips over time. Property tax and insurance are usually escrowed and added on top, along with PMI (if you put down less than 20%) and HOA dues. On a $300,000 property with 20% down at 7% for 30 years, principal and interest alone run $1,596.73 a month — the calculator shows the full stack in a live donut breakdown.

### H2: PMI explained — and when it drops
Private mortgage insurance protects the lender, not you, and it applies when your down payment is under 20%. It typically costs 0.3–1.5% of the loan amount per year, billed monthly. By law (the Homeowners Protection Act), PMI must terminate automatically when your balance amortizes down to 78% of the original property value, and you can request cancellation at 80%. The calculator applies PMI only when your down payment is under 20% and drops it automatically in the schedule the month your balance crosses 78% LTV — you'll see exactly when, and how much PMI you pay in total.

### H2: 15-year vs. 30-year loans for investors
A 15-year loan carries a lower rate and dramatically less total interest, but a much higher payment that eats monthly cash flow. A 30-year loan maximizes cash flow and flexibility — and you can always pay it like a 15-year loan with extra principal payments, without being contractually locked in. Most buy-and-hold investors choose 30-year terms for the cash-flow cushion, then prepay when it suits them. Flip the term select between 30, 20, 15, and 10 years to compare payments and total interest side by side.

### H2: How extra payments save interest
Every extra dollar goes straight to principal, which shrinks the balance that next month's interest is charged on — the savings compound for the entire remaining life of the loan. On a $240,000 loan at 7% for 30 years, just $200 extra per month saves roughly $108,000 in interest and pays the loan off more than 8 years early. The calculator models a recurring monthly extra plus an optional one-time lump sum (a tax refund, a bonus), and shows interest saved, time saved, and your new payoff date next to the baseline.

### H2: What rent coverage means
Before buying a rental, check whether the rent actually covers the full monthly payment — PITI plus HOA. Enter your expected monthly rent and the calculator shows your surplus or shortfall and a coverage percentage. A property at 100% coverage is breaking even on the mortgage alone; vacancy, maintenance, management, and turnover still come out of your pocket, so experienced landlords look for meaningful surplus (lenders' DSCR programs typically want rent at 100–125%+ of the payment). For the full deal analysis, pair this with our [Cap Rate Calculator](/resources/cap-rate-calculator) and [Rental Property ROI Calculator](/resources/rental-property-roi-calculator).

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this mortgage calculator really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Does this work for investment property loans?** Yes — it's built for them. Investment-property loans usually require 15–25% down and rates about 0.5–0.875% above owner-occupied loans; enter your quoted rate and terms and the math is identical. The rent-coverage check is specifically for rentals.
- **H3: How accurate is the PMI estimate?** PMI is estimated as your entered annual percentage of the original loan amount, charged monthly until the balance reaches 78% of the purchase price — the standard automatic-termination point. Your actual PMI rate depends on credit score, LTV, and loan type, so confirm the exact premium with your lender.
- **H3: Are property taxes and insurance included in the payment?** Yes. Enter annual amounts and the calculator escrows them monthly into the total payment, exactly as most servicers do. Investment properties often lose homestead exemptions, so check the assessor's non-exempt rate, and price a landlord (dwelling-fire) policy rather than a standard homeowner's policy.
- **H3: Should I pay extra on the mortgage or invest the cash?** Paying extra earns a guaranteed return equal to your mortgage rate — at 7%+, that's hard to beat risk-free. But many investors prefer keeping cash for reserves or the next down payment. Use the extra-payment comparison to see the exact dollars saved, then weigh it against your alternatives.
- **H3: What's the difference between interest rate and APR?** The interest rate is what the amortization math uses — that's what you enter here. APR bundles the rate with closing costs and fees to make loan offers comparable; it's a shopping tool, not a payment input.
- **H3: How do I compare rate quotes from different lenders?** Use the "What a better rate is worth" table. It re-runs the full amortization at every quarter-point from 1% below to 1% above your current rate and shows the monthly payment and lifetime-interest difference for each — on a $240,000 30-year loan, dropping from 7% to 6.75% saves about $40 a month and roughly $14,400 in interest over the term. Enter each lender's quoted rate, read the savings or cost straight off the table, and share the scenario link with your co-buyer or broker.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator)

## Embed block #2 — JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `RATING_SEED` in the tool's rating widget
> (the rating must match what's visibly displayed on the page — Google requirement).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Mortgage Calculator",
      "url": "https://www.advancedcb.com/resources/mortgage-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "641"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this mortgage calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Does this work for investment property loans?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — it's built for them. Investment-property loans usually require 15–25% down and rates about 0.5–0.875% above owner-occupied loans; enter your quoted rate and terms and the math is identical. The rent-coverage check is specifically for rentals."}},
        {"@type": "Question", "name": "How accurate is the PMI estimate?",
         "acceptedAnswer": {"@type": "Answer", "text": "PMI is estimated as your entered annual percentage of the original loan amount, charged monthly until the balance reaches 78% of the purchase price — the standard automatic-termination point. Confirm the exact premium with your lender."}},
        {"@type": "Question", "name": "Are property taxes and insurance included in the payment?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. Enter annual amounts and the calculator escrows them monthly into the total payment, exactly as most servicers do. Investment properties often lose homestead exemptions, so check the assessor's non-exempt rate."}},
        {"@type": "Question", "name": "Should I pay extra on the mortgage or invest the cash?",
         "acceptedAnswer": {"@type": "Answer", "text": "Paying extra earns a guaranteed return equal to your mortgage rate. Many investors instead keep cash for reserves or the next down payment. Use the extra-payment comparison to see the exact dollars saved, then weigh it against your alternatives."}},
        {"@type": "Question", "name": "What's the difference between interest rate and APR?",
         "acceptedAnswer": {"@type": "Answer", "text": "The interest rate is what the amortization math uses — that's what you enter here. APR bundles the rate with closing costs and fees to make loan offers comparable; it's a shopping tool, not a payment input."}},
        {"@type": "Question", "name": "How do I compare rate quotes from different lenders?",
         "acceptedAnswer": {"@type": "Answer", "text": "Use the \"What a better rate is worth\" table. It re-runs the full amortization at every quarter-point from 1% below to 1% above your current rate and shows the monthly payment and lifetime-interest difference for each — on a $240,000 30-year loan, dropping from 7% to 6.75% saves about $40 a month and roughly $14,400 in interest over the term."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Mortgage Calculator", "item": "https://www.advancedcb.com/resources/mortgage-calculator"}
      ]
    }
  ]
}
</script>
```
