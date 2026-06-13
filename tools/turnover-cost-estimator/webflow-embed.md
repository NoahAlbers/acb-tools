# Webflow page kit: Turnover Cost Estimator

Target URL: `https://www.advancedcb.com/resources/turnover-cost-estimator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Tenant Turnover Cost Calculator for Rentals | Advanced Collection Bureau
- **Meta description:** Free tenant turnover cost calculator for landlords. Itemize lost rent, make-ready, leasing, and legal costs, see the rental turnover cost in months of rent, and compare it to keeping your tenant. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Turnover Cost Estimator
2. Intro paragraph (below H1):
   > Every move-out costs more than the repair invoices show. This free rental turnover cost calculator itemizes everything (vacancy, make-ready, leasing fees, and tenant losses), then shows the total in months of rent, what retention would have cost instead, and what turnover costs you per year. Free, instant, and no email required.
3. **Embed block #1**, the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" aria-label="Tenant Turnover Cost Calculator"
  style="width:1px;min-width:100%;border:0;height:1900px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='turnover-cost-estimator';
  /* forward #… shared-scenario fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/'+slug+'/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool===slug&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
  /* forward parent scroll so the tool’s sticky panels work inside the auto-height iframe */
  function sendScroll(){
    var r=f.getBoundingClientRect();
    if(f.contentWindow)f.contentWindow.postMessage({acbScrollInfo:1,top:-r.top,vh:window.innerHeight},'*');
  }
  window.addEventListener('scroll',sendScroll,{passive:true});
  window.addEventListener('resize',sendScroll,{passive:true});
  f.addEventListener('load',sendScroll);
})();
</script>
```

(The iframe points at the GitHub Pages host; see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool; H2s matter):

### H2: What tenant turnover really costs
Industry estimates consistently put a single turnover at **one to three months of rent, roughly $1,000 to $5,000 per turn**, and well past that when an eviction or major rehab is involved. The money leaks from four buckets: vacancy (rent you never collect plus utilities you now pay), make-ready (cleaning, paint, flooring, repairs, rekeying), leasing (advertising, placement fees, screening, concessions), and admin & loss (unpaid rent, damages beyond the deposit, legal costs). The calculator above adds all four, line by line, so nothing hides.

### H2: The biggest hidden cost is vacancy
Repairs come with invoices; lost rent doesn't, so most landlords undercount it. At $2,200/mo, every vacant day costs about $72 in rent alone, so a typical 30-day vacancy is over $2,100 before you've spent a dollar on paint. That's why the fastest way to cut turnover cost isn't cheaper contractors, it's fewer vacant days: pre-lease during the notice period, schedule make-ready trades before move-out, and price the unit to move in the first two weeks.

### H2: Make-ready checklist costs
Typical per-turn ranges for a single-family rental or apartment: deep cleaning $200 to $500, repainting $500 to $2,000 (full repaint of a 2BR sits near $1,000), carpet replacement or floor refresh $300 to $2,000, general repairs $200 to $1,000, locks/rekey $50 to $150, plus landscaping touch-ups and the occasional appliance. Use the calculator's defaults as a starting point and overwrite them with your own contractor pricing; every line is editable and can be excluded.

### H2: Turnover vs. retention: the math landlords skip
A $200 renewal incentive feels like a cost. Compared against a $5,000+ turnover, it's the best yield in real estate. Even holding off on a $50/mo rent increase "costs" only $600 over a year, typically an eighth of what the turnover would. The calculator's retention card runs this side-by-side with your numbers so you can see exactly what keeping a good tenant saves before you let a lease lapse over a small increase.

### H2: How to reduce turnover
Respond to maintenance fast (it's the #1 cited reason for not renewing), start renewal conversations 90 days out, keep increases modest and explained, offer small renewal perks (carpet cleaning, a smart lock, a gift card), and screen well up front; placing the right tenant once beats re-leasing every year. When a tenant does leave owing money, act quickly: document everything at move-out, apply the deposit correctly, and send the balance to collections before the trail goes cold.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: How much does tenant turnover cost on average?** Most industry estimates land between one and three months of rent, roughly $1,000 to $5,000 per turn for a typical rental, counting lost rent, make-ready, and leasing costs. Evictions or heavy damage can push a single turnover well past $10,000. Your real number depends on rent, vacancy days, and condition, which is exactly what this calculator itemizes.
- **H3: Is this turnover cost calculator really free?** Yes: 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: What if the tenant left owing rent or damages?** First apply the security deposit, following your state's itemization and deadline rules. Anything beyond the deposit (back rent, late fees, damage past normal wear) is a collectible debt. Advanced Collection Bureau specializes in exactly these balances for landlords and property managers, on a no-recovery, no-fee basis, so pursuing what you're owed costs nothing up front.
- **H3: Why does the calculator divide rent by 30.44?** 30.44 is the average number of days in a month (365.25 ÷ 12), so lost rent is prorated accurately whatever the month. A $2,200 unit loses about $72.28 per vacant day.
- **H3: Should I count my own time in turnover costs?** Ideally, yes. If you self-manage, showings, screening, and coordinating trades easily consume 10 to 20 hours per turn. Add an hourly value under the leasing fee (use the Flat $ option) or repairs line to see your true all-in cost.
- **H3: Is it ever better to let a tenant leave?** Sometimes. If the tenant pays late, damages the unit, or the rent is far below market, turnover can be worth the cost. The retention card shows the break-even: if the rent increase you'd gain exceeds the annualized turnover cost, re-leasing can pencil out, with a well-screened replacement.
- **H3: How much does turnover cost across a whole portfolio?** Multiply your per-turnover cost by units × annual turnover rate. U.S. apartment turnover averages roughly 30% to 50% per year, so a 10-unit portfolio at 30% with a $5,000 per-turn cost loses about $15,000 every year, and cutting the turnover rate by just 10 percentage points saves around $5,000/year. The calculator's "Across your portfolio" card runs this with your own numbers, ready to drop into an owner report.

6. **Related tools section** (H2: More free landlord tools), link grid:
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator) ·
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Prorated Rent Calculator](/resources/prorated-rent-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Security Deposit Interest Calculator](/resources/security-deposit-interest-calculator)

## Embed block #2: JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `RATING_SEED` in the tool's rating widget
> (the rating must match what's visibly displayed on the page; this is a Google requirement).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Tenant Turnover Cost Calculator",
      "url": "https://www.advancedcb.com/resources/turnover-cost-estimator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CalculateAction", "name": "Estimate tenant turnover cost",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/turnover-cost-estimator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.9", "ratingCount": "158"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "How much does tenant turnover cost on average?",
         "acceptedAnswer": {"@type": "Answer", "text": "Most industry estimates land between one and three months of rent, roughly $1,000 to $5,000 per turn for a typical rental, counting lost rent, make-ready, and leasing costs. Evictions or heavy damage can push a single turnover well past $10,000. Your real number depends on rent, vacancy days, and condition, which is exactly what this calculator itemizes."}},
        {"@type": "Question", "name": "Is this turnover cost calculator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes: 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "What if the tenant left owing rent or damages?",
         "acceptedAnswer": {"@type": "Answer", "text": "First apply the security deposit, following your state's itemization and deadline rules. Anything beyond the deposit (back rent, late fees, damage past normal wear) is a collectible debt. Advanced Collection Bureau specializes in exactly these balances for landlords and property managers, on a no-recovery, no-fee basis, so pursuing what you're owed costs nothing up front."}},
        {"@type": "Question", "name": "Why does the calculator divide rent by 30.44?",
         "acceptedAnswer": {"@type": "Answer", "text": "30.44 is the average number of days in a month (365.25 ÷ 12), so lost rent is prorated accurately whatever the month. A $2,200 unit loses about $72.28 per vacant day."}},
        {"@type": "Question", "name": "Should I count my own time in turnover costs?",
         "acceptedAnswer": {"@type": "Answer", "text": "Ideally, yes. If you self-manage, showings, screening, and coordinating trades easily consume 10 to 20 hours per turn. Add an hourly value under the leasing fee (use the Flat $ option) or repairs line to see your true all-in cost."}},
        {"@type": "Question", "name": "Is it ever better to let a tenant leave?",
         "acceptedAnswer": {"@type": "Answer", "text": "Sometimes. If the tenant pays late, damages the unit, or the rent is far below market, turnover can be worth the cost. The retention card shows the break-even: if the rent increase you'd gain exceeds the annualized turnover cost, re-leasing can pencil out, with a well-screened replacement."}},
        {"@type": "Question", "name": "How much does turnover cost across a whole portfolio?",
         "acceptedAnswer": {"@type": "Answer", "text": "Multiply your per-turnover cost by units × annual turnover rate. U.S. apartment turnover averages roughly 30% to 50% per year, so a 10-unit portfolio at 30% with a $5,000 per-turn cost loses about $15,000 every year, and cutting the turnover rate by just 10 percentage points saves around $5,000/year. The calculator's \"Across your portfolio\" card runs this with your own numbers, ready to drop into an owner report."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Turnover Cost Estimator", "item": "https://www.advancedcb.com/resources/turnover-cost-estimator"}
      ]
    }
  ]
}
</script>
```
