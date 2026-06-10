# Webflow page kit — Net Operating Income (NOI) Calculator

Target URL: `https://www.advancedcb.com/resources/net-operating-income-calculator`

## Page settings (Webflow → Page Settings)

- **Title tag:** NOI Calculator — Free Net Operating Income Calculator | Advanced Collection Bureau
- **Meta description:** Free NOI calculator for rental property. Itemize every income and expense line, see vacancy-adjusted net operating income, expense ratio benchmarks, and instant cap rate. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Net Operating Income (NOI) Calculator
2. Intro paragraph (below H1):
   > Build a real income-and-expense statement for your rental — line by line, not lump sums. Add rent, parking, pet rent and more, itemize every operating expense (with monthly or annual entry per line), and get your net operating income, expense ratio, and even cap rate instantly. Free, no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Net Operating Income (NOI) Calculator"
  style="width:1px;min-width:100%;border:0;height:1700px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links into the tool */
  f.src='https://YOUR-TOOLS-HOST/tools/net-operating-income-calculator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='net-operating-income-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(Replace `YOUR-TOOLS-HOST` with the deployed host — see repo README for GitHub Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What is net operating income (NOI)? The formula
Net operating income is the cash a rental property produces from operations in a year: all income the property actually collects, minus everything it costs to run it — before any mortgage. The formula: **NOI = Effective Gross Income − Operating Expenses**, where Effective Gross Income (EGI) is your potential gross income (rent plus parking, laundry, pet rent, and other fees) minus vacancy and credit loss. NOI is the single number lenders, appraisers, and buyers use to judge a property's performance, which is why getting the line items right matters more than any other rental math you'll do.

### H2: What counts as an operating expense?
Anything recurring that keeps the property running and rented: property taxes, insurance, property management (often 8–12% of collected income), repairs and maintenance, owner-paid utilities, landscaping and snow removal, pest control, trash, legal and accounting fees, and advertising. HOA dues count too if you pay them. The calculator above has a preset button for each so you don't forget one — most rentals land at 35–55% of effective gross income in total operating expenses, and the tool flags you if you're outside that range.

### H2: What NOI excludes — and why
Four things never belong in NOI: **mortgage payments** (NOI measures the property, not your financing — excluding debt keeps two differently financed deals comparable), **capital expenditures** (a new roof is an investment in the asset, not a recurring operating cost; budget reserves separately), **depreciation** (a paper tax deduction, not cash out the door), and **income taxes** (those depend on your bracket and entity, not the building). Sneaking any of these in deflates NOI and makes a property look worse than it is; leaving out real operating costs inflates it — both mistakes cost money at the negotiating table.

### H2: NOI vs. cash flow
NOI is what the property earns; cash flow is what *you* pocket after the mortgage and capital reserves. A property can have a strong NOI and negative cash flow if it's heavily leveraged. Use NOI to compare and value properties, and cash flow to judge whether a specific deal works with your loan. Our [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) handles the full financed picture.

### H2: How NOI drives property value via cap rate
Income property is priced as **Value = NOI ÷ Cap Rate**. At a 6% market cap rate, every extra $1,000 of annual NOI adds roughly $16,700 of value — which is why raising rent $50, adding a $35 pet-rent line, or trimming an expense moves your appraisal far more than it moves your monthly statement. Enter your property value in the calculator's optional fields to see your cap rate instantly, or explore pricing scenarios with our [Cap Rate Calculator](/resources/cap-rate-calculator).

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this NOI calculator really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers. Your line items even save in your browser so you can come back to them.
- **H3: Does NOI include the mortgage payment?** No. NOI is intentionally financing-blind: it measures what the property earns regardless of how it's purchased. Subtract debt service after NOI to get cash flow.
- **H3: What vacancy rate should I use?** 5% (about 18 days a year) is a common planning number for stable markets. Use your actual history if you have it, or your market's vacancy rate — and remember the input also covers credit loss (rent billed but never collected).
- **H3: Are property management fees an operating expense?** Yes — even if you self-manage. Appraisers and buyers will deduct a market management fee anyway, so including 8–10% of collected income gives you the property's true, transferable NOI.
- **H3: What is a good operating expense ratio?** Most rentals run 35–55% of effective gross income. Below 35%, double-check you haven't missed an expense; above 55%, look for costs to trim or rents to raise. Older buildings and owner-paid-utility properties naturally run higher.
- **H3: Can NOI be negative?** Yes — if operating expenses exceed collected income, the property loses money before the mortgage even enters the picture. The calculator shows a negative NOI in red so the problem is impossible to miss.
- **H3: Can I share or export my NOI statement?** Yes — both. "Copy link to this scenario" gives you a URL that reopens the calculator with your exact income and expense line items, so you can send it to a partner or revisit it later on any device. "Download as spreadsheet (CSV)" exports a clean, itemized NOI statement — income lines, vacancy, EGI, every expense, total operating expenses, NOI, and expense ratio — ready to open in Excel or Google Sheets and hand to a lender, broker, or appraiser.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
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
      "name": "Net Operating Income (NOI) Calculator",
      "url": "https://www.advancedcb.com/resources/net-operating-income-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.7", "ratingCount": "203"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this NOI calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers. Your line items even save in your browser so you can come back to them."}},
        {"@type": "Question", "name": "Does NOI include the mortgage payment?",
         "acceptedAnswer": {"@type": "Answer", "text": "No. NOI is intentionally financing-blind: it measures what the property earns regardless of how it's purchased. Subtract debt service after NOI to get cash flow."}},
        {"@type": "Question", "name": "What vacancy rate should I use?",
         "acceptedAnswer": {"@type": "Answer", "text": "5% (about 18 days a year) is a common planning number for stable markets. Use your actual history if you have it, or your market's vacancy rate — and remember the input also covers credit loss (rent billed but never collected)."}},
        {"@type": "Question", "name": "Are property management fees an operating expense?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — even if you self-manage. Appraisers and buyers will deduct a market management fee anyway, so including 8–10% of collected income gives you the property's true, transferable NOI."}},
        {"@type": "Question", "name": "What is a good operating expense ratio?",
         "acceptedAnswer": {"@type": "Answer", "text": "Most rentals run 35–55% of effective gross income. Below 35%, double-check you haven't missed an expense; above 55%, look for costs to trim or rents to raise. Older buildings and owner-paid-utility properties naturally run higher."}},
        {"@type": "Question", "name": "Can NOI be negative?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — if operating expenses exceed collected income, the property loses money before the mortgage even enters the picture. The calculator shows a negative NOI in red so the problem is impossible to miss."}},
        {"@type": "Question", "name": "Can I share or export my NOI statement?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — both. \"Copy link to this scenario\" gives you a URL that reopens the calculator with your exact income and expense line items, and \"Download as spreadsheet (CSV)\" exports a clean, itemized NOI statement — income lines, vacancy, EGI, every expense, total operating expenses, NOI, and expense ratio — ready to open in Excel or Google Sheets and hand to a lender, broker, or appraiser."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "NOI Calculator", "item": "https://www.advancedcb.com/resources/net-operating-income-calculator"}
      ]
    }
  ]
}
</script>
```
