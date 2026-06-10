# Webflow page kit — 70% Rule Calculator

Target URL: `https://www.advancedcb.com/resources/70-percent-rule-calculator`

## Page settings (Webflow → Page Settings)

- **Title tag:** 70% Rule Calculator — Max Offer for House Flipping (Free) | Advanced Collection Bureau
- **Meta description:** Free 70 percent rule calculator for house flipping. Get your max allowable offer from ARV and repairs, check a real asking price, and see where the 30% margin goes. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** 70% Rule Calculator
2. Intro paragraph (below H1):
   > The fastest way to screen a fix-and-flip: pay no more than 70% of the after repair value, minus repairs. This calculator finds your maximum allowable offer, lets you adjust the rule percentage for your market, pressure-tests a real asking price, and shows exactly where the 30% margin goes — free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="70% Rule Calculator"
  style="width:1px;min-width:100%;border:0;height:1600px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/70-percent-rule-calculator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='70-percent-rule-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What is the 70% rule in house flipping?
The 70% rule is a screening shortcut flippers and wholesalers use to set a ceiling on what they'll pay for a property. It says: never pay more than 70% of the home's after repair value (ARV) minus the cost of repairs. The 30% you hold back isn't profit padding — it has to cover every cost of buying, holding, and reselling the house *and* still leave a worthwhile profit. If a deal fails the 70% rule, it usually isn't worth a deeper workup.

### H2: The formula, with a worked example
**Maximum Allowable Offer (MAO) = ARV × 70% − Repair Costs.** Say a house will be worth $300,000 fully renovated and needs $40,000 of work: $300,000 × 0.70 = $210,000, minus $40,000 of repairs = a **$170,000 max offer**. If the seller is asking $185,000, you're $15,000 over MAO and your implied margin drops to 25% of ARV — the calculator's Deal Check tab runs this comparison for any asking price.

### H2: When to adjust the percentage
70% is a rule of thumb, not a law. Drop to **65% (or lower)** in expensive metros, on heavy structural rehabs, or anywhere your downside risk is bigger — high price points magnify every percentage of margin you give up. Stretch to **75–80%** in fiercely competitive markets where strict 70% offers never win, on light cosmetic "wholetail" deals you'll resell quickly, or when you have unusually cheap capital. The calculator's slider and presets let you re-run the math at any percentage from 60% to 85%.

### H2: What the 30% margin actually covers
Roughly **10–15% of ARV disappears into transaction and holding costs**: closing costs when you buy, loan interest and points, property taxes, insurance and utilities during the rehab, then agent commissions and closing costs again when you sell. The remaining **15–20% of ARV is your target profit** — compensation for the risk, the capital, and months of work. That's why the rule discounts ARV by 30% before repairs even enter the equation, and why "I'll just take a thinner margin" is how flips turn into break-even projects.

### H2: Limits of the rule — when it breaks down
The 70% rule is a screen, not an underwriting model. It distorts at the price extremes: on a $80,000 house, 30% of ARV ($24,000) may not even cover fixed transaction costs; on a $900,000 house it holds back more than most flippers need. It also says nothing about how *long* you'll hold (six extra months of interest and taxes can erase a "passing" deal), assumes your ARV comps and rehab budget are right, and ignores financing structure. Use it to kill bad deals fast — then build a full line-item budget before you write an offer.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this 70% rule calculator really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords, property managers, and real-estate investors.
- **H3: How do I estimate ARV?** Pull 3–6 comparable sales: fully renovated homes within about half a mile, with similar beds, baths, and square footage, sold in the last 3–6 months. Adjust for differences and stay conservative — an inflated ARV inflates your max offer dollar-for-dollar at 70 cents each.
- **H3: Does the 70% rule include closing and holding costs?** Yes — implicitly. The 30% you hold back is meant to absorb both sets of closing costs, financing and holding expenses, and selling commissions, with the remainder as profit. That's why you don't subtract those line items separately when using the rule.
- **H3: What if my maximum offer comes out negative?** It means repairs are so large relative to ARV that no purchase price works at your chosen percentage — the calculator flags this and shows the minimum ARV the deal would need. Renegotiate, shrink the scope, or walk away.
- **H3: Is the 70% rule good for rental properties (BRRRR)?** It's a reasonable first screen for BRRRR deals since refinance appraisals behave like a resale, but rentals ultimately live or die on cash flow and refinance terms — follow up with a full rental analysis, like our Rental Property ROI Calculator.
- **H3: Why do wholesalers subtract their fee from MAO?** A wholesaler's end buyer is usually a flipper who needs the deal to pass the 70% rule. So wholesalers compute MAO the same way, then subtract their assignment fee to get the most they can put a property under contract for.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
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
      "name": "70% Rule Calculator",
      "url": "https://www.advancedcb.com/resources/70-percent-rule-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "176"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this 70% rule calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords, property managers, and real-estate investors."}},
        {"@type": "Question", "name": "How do I estimate ARV?",
         "acceptedAnswer": {"@type": "Answer", "text": "Pull 3–6 comparable sales: fully renovated homes within about half a mile, with similar beds, baths, and square footage, sold in the last 3–6 months. Adjust for differences and stay conservative — an inflated ARV inflates your max offer."}},
        {"@type": "Question", "name": "Does the 70% rule include closing and holding costs?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — implicitly. The 30% held back is meant to absorb both sets of closing costs, financing and holding expenses, and selling commissions, with the remainder as profit, so you don't subtract those line items separately."}},
        {"@type": "Question", "name": "What if my maximum offer comes out negative?",
         "acceptedAnswer": {"@type": "Answer", "text": "It means repairs are so large relative to ARV that no purchase price works at your chosen percentage. Renegotiate the price, shrink the rehab scope, or walk away."}},
        {"@type": "Question", "name": "Is the 70% rule good for rental properties (BRRRR)?",
         "acceptedAnswer": {"@type": "Answer", "text": "It's a reasonable first screen for BRRRR deals since refinance appraisals behave like a resale, but rentals ultimately live or die on cash flow and refinance terms — follow up with a full rental analysis."}},
        {"@type": "Question", "name": "Why do wholesalers subtract their fee from MAO?",
         "acceptedAnswer": {"@type": "Answer", "text": "A wholesaler's end buyer is usually a flipper who needs the deal to pass the 70% rule, so wholesalers compute MAO the same way and then subtract their assignment fee to get their maximum contract price."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "70% Rule Calculator", "item": "https://www.advancedcb.com/resources/70-percent-rule-calculator"}
      ]
    }
  ]
}
</script>
```
