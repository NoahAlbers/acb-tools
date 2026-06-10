# Webflow page kit — Prorated Rent Calculator

Target URL: `https://www.advancedcb.com/resources/prorated-rent-calculator`

> **Note:** this kit **replaces the existing calculator embed** on the live page (the old
> Webflow-embed version). Swap the embed block only — the page's existing FAQ accordion can stay
> (the FAQ copy below matches/refreshes it). Old shared links that used
> `?rent=…&date=…&billon=…` query params still work: the new tool reads them on load.

## Page settings (Webflow → Page Settings)

- **Title tag:** Prorated Rent Calculator — Free, Instant & No Signup | Advanced Collection Bureau
- **Meta description:** Free prorated rent calculator for landlords and tenants. Handles any billing day, 28–31 day months, leap years, and move-outs — with day-by-day math you can show your tenant. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Prorated Rent Calculator
2. Intro paragraph (below H1):
   > Moving in (or out) mid-month? Enter the monthly rent, the move-in date, and the day rent is normally billed — the calculator instantly shows the partial rent due, the daily rate, and exactly which days are being charged. Free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Prorated Rent Calculator"
  style="width:1px;min-width:100%;border:0;height:1200px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/prorated-rent-calculator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='prorated-rent-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What is prorated rent?
Prorated rent is a partial month's rent, charged when a tenant occupies a unit for only part of a billing cycle — most commonly a mid-month move-in. Instead of paying a full month, the tenant pays a daily rate (monthly rent ÷ days in that month) for each day from the move-in date through the day before the next regular billing date.

### H2: The prorated rent formula (with a worked example)
**Daily rate = monthly rent ÷ days in that calendar month. Prorated rent = daily rate × billable days.** Example: rent is $1,500, the tenant moves in July 15, and rent is billed on the 1st. July has 31 days, so the daily rate is $1,500 ÷ 31 = $48.39. The tenant owes July 15–31 = 17 days × $48.39 = **$822.58**, and the first full month is billed August 1.

### H2: What if rent is billed on a day other than the 1st?
Many leases bill on the anniversary of move-in or another fixed day. The math is the same — the prorated period runs from the move-in date through the day before the next billing date — but it can cross into the next month. When that happens, the calculator charges each day at *its own month's* daily rate. Example: $1,500 rent, move-in July 20, billed on the 15th → 12 July days + 14 August days at $48.39/day = **$1,258.06**, with the first full cycle billed August 15.

### H2: Month lengths and leap years
A "month" can be 28, 29, 30, or 31 days, so a flat daily rate is never quite right. This calculator always divides by the actual number of days in the calendar month in question — including 29 days for February in leap years — so the daily rate is exact for every month. (Some landlords prefer a 30-day "banker's month" or a 365-day annualized rate; if your lease specifies one of those, follow the lease.)

### H2: Does this work for move-outs?
Yes. On a move-out, the tenant owes rent from the regular billing date through the last day of occupancy, at the same daily rate. Quick trick: enter the day *after* the move-out as the "move-in date" — the result is the slice of the cycle the tenant does **not** owe; subtract it from a full month's rent (exact whenever the cycle stays within one calendar month). The tool's move-out tooltip walks through an example.

5. **FAQ section** (H2: Frequently Asked Questions; the page's existing accordion can stay — sync its copy to this):

- **H3: What is prorated rent?** Prorated rent is a partial month's rent for the days a tenant actually occupies the unit — typically charged when someone moves in after the regular billing date. It equals the daily rate (monthly rent ÷ days in that month) times the number of days from move-in through the day before the next billing date.
- **H3: How do I calculate prorated rent?** Divide the monthly rent by the number of days in that calendar month to get the daily rate, then multiply by the billable days. Example: $1,500 rent, move-in July 15, billed on the 1st → $1,500 ÷ 31 = $48.39/day × 17 days = $822.58.
- **H3: What if my billing date isn't the 1st?** The prorated period runs from your move-in date through the day before the next billing date, even when that crosses into the next month. The calculator charges each day at that month's own daily rate, so cross-month periods are handled exactly.
- **H3: How does the calculator handle 28–31 days and leap years?** It always uses the actual number of days in each calendar month — 28 or 29 for February (29 in leap years), 30 or 31 elsewhere — so the daily rate is exact for every month rather than an approximation.
- **H3: What if my billing day is the 31st?** In months with fewer than 31 days, the bill simply falls on the last day of that month, and the prorated period counts up to the day before. The calculator adjusts this automatically.
- **H3: Does this calculator work for move-outs?** Yes. For a move-out you owe rent from your billing date through your last day. Enter the day after your move-out as the "move-in date" — the result is the portion of the cycle you don't owe; subtract it from a full month's rent (exact when the billing cycle stays within one calendar month).

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter](/resources/security-deposit-return-letter-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Security Deposit Interest Calculator](/resources/security-deposit-interest-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

## Embed block #2 — JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `SEED` in the tool's rating widget
> (currently **4.8 / 426** — the rating must match what's visibly displayed on the page — Google requirement).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Prorated Rent Calculator",
      "url": "https://www.advancedcb.com/resources/prorated-rent-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "426"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "What is prorated rent?",
         "acceptedAnswer": {"@type": "Answer", "text": "Prorated rent is a partial month's rent for the days a tenant actually occupies the unit — typically charged when someone moves in after the regular billing date. It equals the daily rate (monthly rent ÷ days in that month) times the number of days from move-in through the day before the next billing date."}},
        {"@type": "Question", "name": "How do I calculate prorated rent?",
         "acceptedAnswer": {"@type": "Answer", "text": "Divide the monthly rent by the number of days in that calendar month to get the daily rate, then multiply by the billable days. Example: $1,500 rent, move-in July 15, billed on the 1st → $1,500 ÷ 31 = $48.39/day × 17 days = $822.58."}},
        {"@type": "Question", "name": "What if my billing date isn't the 1st?",
         "acceptedAnswer": {"@type": "Answer", "text": "The prorated period runs from your move-in date through the day before the next billing date, even when that crosses into the next month. The calculator charges each day at that month's own daily rate, so cross-month periods are handled exactly."}},
        {"@type": "Question", "name": "How does the calculator handle 28–31 days and leap years?",
         "acceptedAnswer": {"@type": "Answer", "text": "It always uses the actual number of days in each calendar month — 28 or 29 for February (29 in leap years), 30 or 31 elsewhere — so the daily rate is exact for every month rather than an approximation."}},
        {"@type": "Question", "name": "What if my billing day is the 31st?",
         "acceptedAnswer": {"@type": "Answer", "text": "In months with fewer than 31 days, the bill simply falls on the last day of that month, and the prorated period counts up to the day before. The calculator adjusts this automatically."}},
        {"@type": "Question", "name": "Does this calculator work for move-outs?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. For a move-out you owe rent from your billing date through your last day. Enter the day after your move-out as the \"move-in date\" — the result is the portion of the cycle you don't owe; subtract it from a full month's rent (exact when the billing cycle stays within one calendar month)."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Prorated Rent Calculator", "item": "https://www.advancedcb.com/resources/prorated-rent-calculator"}
      ]
    }
  ]
}
</script>
```
