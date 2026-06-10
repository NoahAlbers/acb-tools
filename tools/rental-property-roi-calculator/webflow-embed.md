# Webflow page kit — Rental Property ROI Calculator

Target URL: `https://www.advancedcb.com/resources/rental-property-roi-calculator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Rental Property ROI Calculator — Free Cash Flow & IRR Tool
- **Meta description:** Free rental property calculator for landlords and investors. Get monthly cash flow, cash-on-cash return, cap rate, IRR, and a year-by-year projection — no signup, no email.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Rental Property ROI Calculator
2. Intro paragraph (below H1):
   > Run the full numbers on a rental in seconds: monthly cash flow, cash-on-cash return, cap rate, and the annualized return (IRR) you'd actually earn through sale — including loan paydown and appreciation. Charts, a year-by-year table, and plain-English explanations of every term. Free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Rental Property ROI Calculator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links into the tool */
  f.src='https://YOUR-TOOLS-HOST/tools/rental-property-roi-calculator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='rental-property-roi-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(Replace `YOUR-TOOLS-HOST` with the deployed host — see repo README for GitHub Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: How to analyze a rental property
Start with three questions: does it cash flow, what does your cash earn, and what is the total return at sale? Take the gross rent, subtract a realistic vacancy allowance (about 5%), then subtract operating expenses — taxes, insurance, maintenance, a CapEx reserve, management, and any owner-paid utilities or HOA. That leaves net operating income (NOI). Subtract the mortgage payment and you have cash flow. Finally, project value growth and loan paydown over your hold period to see the full return. The calculator above does every step live and shows the year-by-year math.

### H2: What is cash-on-cash return?
Cash-on-cash return is your first-year cash flow divided by the total cash you actually invested — down payment, closing costs, and up-front repairs. Unlike cap rate, it includes your mortgage, so it answers the question investors care about most: "what is the cash I put in earning?" Formula: **Cash-on-Cash = Annual Cash Flow ÷ Total Cash Invested × 100**.

### H2: What is a good ROI on rental property?
There's no universal number, but useful anchors: many buy-and-hold investors look for 5–8%+ cash-on-cash in year one, and a total IRR (including loan paydown, appreciation, and sale) of 10–15%+ over a long hold. Markets differ — appreciation-heavy metros often have thin or negative early cash flow, while cash-flow markets offer higher yields with slower value growth. Compare against your alternatives: if a deal's IRR can't beat a boring index fund, the headaches need to be worth something.

### H2: The 1% rule explained
The 1% rule is a 10-second screen: a property's monthly rent should be at least 1% of its purchase price ($2,500/mo on a $250,000 house). Properties that pass have a good shot at positive cash flow with conventional financing; properties far below it rarely pencil. It's a filter, not a verdict — taxes, insurance, and rates vary too much to skip the full analysis. The calculator shows a pass/fail check automatically.

### H2: How IRR works for rentals
Internal rate of return (IRR) is the single annual rate that explains every cash flow in the deal: the cash you put in at purchase (negative), the cash flow you collect each year, and the net proceeds when you sell (sale price minus selling costs and the remaining loan balance). It captures what cash-on-cash misses — equity built by the tenant paying down your loan, and appreciation — which is why a rental with modest monthly cash flow can still post a double-digit IRR. Our calculator computes IRR for your chosen hold period and for every year in the table, so you can see when selling makes sense.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this rental property calculator really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Does the calculator include mortgage payments?** Yes. Enter your down payment, rate, and term and it computes the monthly principal & interest, full amortization, the loan balance in every year, and your payoff at sale. Toggle the loan off for an all-cash analysis.
- **H3: What's a good cash-on-cash return for a rental?** Many investors target 5–8%+ in year one, but it depends on the market and your goals. Appreciation markets often start lower; cash-flow markets higher. Judge the full IRR over your hold period, not just year one.
- **H3: Why is my IRR higher than my cash-on-cash return?** Because cash-on-cash only counts the rent left over each month, while IRR also counts the loan being paid down with the tenant's rent and the property appreciating — both of which you collect when you sell.
- **H3: What expenses should I include?** Property taxes, insurance, maintenance, a CapEx reserve for big-ticket items (roof, HVAC), property management, owner-paid utilities, HOA dues, and a vacancy allowance. Forgetting CapEx and vacancy is the most common way new landlords overestimate returns.
- **H3: Can I save and compare multiple deals?** Yes — free, no account needed. Save each scenario with a name (up to 8) and the calculator builds a side-by-side comparison table of price, rent, monthly cash flow, cash-on-cash, cap rate, NOI, IRR, and cash invested, with the best number in each row highlighted. You can also copy a share link that reopens the calculator with your exact inputs, and run a one-click stress test (vacancy doubled, rate +1%, rent −10%) to see whether the deal still cash-flows. Everything is stored in your browser — nothing is uploaded.
- **H3: How accurate are the projections?** They're as good as your assumptions. The math (amortization, NOI, IRR) is exact; rents, expenses, and appreciation are estimates you control. Test conservative numbers — a deal that only works at 5% appreciation isn't a cash-flow deal, it's a bet.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
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
      "name": "Rental Property ROI Calculator",
      "url": "https://www.advancedcb.com/resources/rental-property-roi-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.9", "ratingCount": "487"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this rental property calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Does the calculator include mortgage payments?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. Enter your down payment, rate, and term and it computes the monthly principal & interest, full amortization, the loan balance in every year, and your payoff at sale. Toggle the loan off for an all-cash analysis."}},
        {"@type": "Question", "name": "What's a good cash-on-cash return for a rental?",
         "acceptedAnswer": {"@type": "Answer", "text": "Many investors target 5–8%+ in year one, but it depends on the market and your goals. Appreciation markets often start lower; cash-flow markets higher. Judge the full IRR over your hold period, not just year one."}},
        {"@type": "Question", "name": "Why is my IRR higher than my cash-on-cash return?",
         "acceptedAnswer": {"@type": "Answer", "text": "Because cash-on-cash only counts the rent left over each month, while IRR also counts the loan being paid down with the tenant's rent and the property appreciating — both of which you collect when you sell."}},
        {"@type": "Question", "name": "What expenses should I include?",
         "acceptedAnswer": {"@type": "Answer", "text": "Property taxes, insurance, maintenance, a CapEx reserve for big-ticket items (roof, HVAC), property management, owner-paid utilities, HOA dues, and a vacancy allowance. Forgetting CapEx and vacancy is the most common way new landlords overestimate returns."}},
        {"@type": "Question", "name": "Can I save and compare multiple deals?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — free, no account needed. Save each scenario with a name (up to 8) and the calculator builds a side-by-side comparison table of price, rent, monthly cash flow, cash-on-cash, cap rate, NOI, IRR, and cash invested, with the best number in each row highlighted. You can also copy a share link that reopens the calculator with your exact inputs, and run a one-click stress test (vacancy doubled, rate +1%, rent −10%). Everything is stored in your browser — nothing is uploaded."}},
        {"@type": "Question", "name": "How accurate are the projections?",
         "acceptedAnswer": {"@type": "Answer", "text": "They're as good as your assumptions. The math (amortization, NOI, IRR) is exact; rents, expenses, and appreciation are estimates you control. Test conservative numbers before you buy."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Rental Property ROI Calculator", "item": "https://www.advancedcb.com/resources/rental-property-roi-calculator"}
      ]
    }
  ]
}
</script>
```
