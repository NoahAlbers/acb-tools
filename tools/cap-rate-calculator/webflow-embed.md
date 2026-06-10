# Webflow page kit — Cap Rate Calculator

Target URL: `https://www.advancedcb.com/resources/cap-rate-calculator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Cap Rate Calculator — Free, Instant & No Signup | Advanced Collection Bureau
- **Meta description:** Free cap rate calculator for rental property investors. Solve cap rate, max purchase price, or required NOI — with a built-in NOI helper and sensitivity table. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Cap Rate Calculator
2. Intro paragraph (below H1):
   > Quickly measure a rental property's return with the industry-standard capitalization rate. Solve for the cap rate itself, the most you should pay to hit a target return, or the income a property needs to pencil out — free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" src="https://YOUR-TOOLS-HOST/tools/cap-rate-calculator/"
  title="Cap Rate Calculator" style="width:1px;min-width:100%;border:0;height:1400px"
  loading="eager"></iframe>
<script>
window.addEventListener('message',function(e){
  if(e.data&&e.data.acbTool==='cap-rate-calculator'){
    var f=document.getElementById('acb-tool-frame');
    if(f) f.style.height=(e.data.height+2)+'px';
  }
});
</script>
```

(Replace `YOUR-TOOLS-HOST` with the deployed host — see repo README for GitHub Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What is a cap rate?
The capitalization rate is a property's annual net operating income (NOI) divided by its price. It tells you the return the property itself produces before any mortgage — which makes it the fastest way to compare two deals apples-to-apples. Formula: **Cap Rate = NOI ÷ Property Value × 100**.

### H2: What is a good cap rate for rental property?
There's no single "good" number — it's a risk dial. 4–7% is typical for stable buy-and-hold rentals in decent markets; below 4% usually means a premium location with low risk and low income; 8–10%+ usually signals higher risk, heavier management, or a market with declining values. Compare against similar properties in the same submarket, not a national average.

### H2: Cap rate vs. cash-on-cash return
Cap rate ignores financing; cash-on-cash measures the return on the actual cash you put in after mortgage payments. Use cap rate to compare properties, cash-on-cash to judge your deal with your loan. Our [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) computes both.

### H2: How to calculate NOI
Add up all income (rent, parking, laundry, pet rent), subtract vacancy, then subtract operating expenses — property tax, insurance, maintenance, management, owner-paid utilities, HOA. Do **not** subtract mortgage payments, depreciation, or capital improvements. The calculator's "Help me calculate NOI" panel does this for you, or use the dedicated [NOI Calculator](/resources/net-operating-income-calculator).

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this cap rate calculator really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Does cap rate include the mortgage?** No. Cap rate is intentionally financing-blind so you can compare properties regardless of how they're purchased. Debt service belongs in cash-on-cash and DSCR analysis.
- **H3: Should I use purchase price or market value?** For a purchase decision, use the price you'd actually pay (including known immediate repairs for an "all-in" view). For a property you already own, use current market value to see what your equity is earning.
- **H3: What expenses count as operating expenses?** Property taxes, insurance, repairs and maintenance, property management, owner-paid utilities, HOA dues, landscaping, pest control, legal/accounting, and advertising. Mortgage payments, capital expenditures, depreciation, and income taxes are excluded.
- **H3: Why do cap rates differ between cities?** Investors accept lower yields where risk is lower and appreciation is stronger, and demand higher yields where vacancy, taxes, or volatility are higher. That's why a 5% cap can be great in one metro and terrible in another.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
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
      "name": "Cap Rate Calculator",
      "url": "https://www.advancedcb.com/resources/cap-rate-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "312"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this cap rate calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Does cap rate include the mortgage?",
         "acceptedAnswer": {"@type": "Answer", "text": "No. Cap rate is intentionally financing-blind so you can compare properties regardless of how they're purchased. Debt service belongs in cash-on-cash and DSCR analysis."}},
        {"@type": "Question", "name": "Should I use purchase price or market value?",
         "acceptedAnswer": {"@type": "Answer", "text": "For a purchase decision, use the price you'd actually pay. For a property you already own, use current market value to see what your equity is earning."}},
        {"@type": "Question", "name": "What expenses count as operating expenses?",
         "acceptedAnswer": {"@type": "Answer", "text": "Property taxes, insurance, repairs and maintenance, property management, owner-paid utilities, HOA dues, landscaping, pest control, legal/accounting, and advertising. Mortgage payments, capital expenditures, depreciation, and income taxes are excluded."}},
        {"@type": "Question", "name": "Why do cap rates differ between cities?",
         "acceptedAnswer": {"@type": "Answer", "text": "Investors accept lower yields where risk is lower and appreciation is stronger, and demand higher yields where vacancy, taxes, or volatility are higher."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Cap Rate Calculator", "item": "https://www.advancedcb.com/resources/cap-rate-calculator"}
      ]
    }
  ]
}
</script>
```
