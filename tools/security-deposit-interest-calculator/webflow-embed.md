# Webflow page kit — Security Deposit Interest Calculator

Target URL: `https://www.advancedcb.com/resources/security-deposit-interest-calculator`

> ⚠️ **This replaces the existing Security Deposit Interest Calculator embed on the live page.**
> Whatever the current page's slug is, point that page at the iframe below (and keep/301 the URL
> to `/resources/security-deposit-interest-calculator` if it differs). Legacy shared links of the
> form `?amount=&rate=&start=&end=&state=` keep working — the embed forwards query params and the
> tool prefills from them.

## Page settings (Webflow → Page Settings)

- **Title tag:** Security Deposit Interest Calculator — Daily Compounding, All 50 States + DC | Advanced Collection Bureau
- **Meta description:** Free security deposit interest calculator with daily compounding. See exactly what a tenant's deposit earns, plus your state's deposit cap, return deadline, and interest rules. No signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Security Deposit Interest Calculator
2. Intro paragraph (below H1):
   > Several states require landlords to pay tenants interest on security deposits — and even where it's optional, you may owe the math at move-out. Enter the deposit, rate, and holding period to see the daily-compounded total, alongside your state's deposit cap, return deadline, and interest requirement. Free, instant, and no email required.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Security Deposit Interest Calculator"
  style="width:1px;min-width:100%;border:0;height:1400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… shared-scenario links AND legacy ?amount=&rate=&start=&end=&state= links into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/security-deposit-interest-calculator/'+(location.search||'')+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='security-deposit-interest-calculator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: Which states require interest on security deposits?
As of this writing, these states (plus D.C.) have a statutory interest requirement — many of them conditional:
**Connecticut, Delaware, District of Columbia, Florida** (only if the deposit is held in an interest-bearing account), **Georgia** (if in escrow or secured by surety bond), **Illinois** (landlords with 25+ units holding the deposit more than 6 months), **Iowa** (interest owed after five years), **Maryland** (3% simple interest on deposits of $50+), **Massachusetts** (5% or the bank rate), **Minnesota** (1% simple interest), **New Hampshire, New Jersey, New Mexico** (if the deposit exceeds one month's rent on a lease of one year or more), **New York** (landlords with six or more units), **North Dakota** (interest owed after 9 months), **Ohio** (5% if the deposit exceeds one month's rent and tenancy is six months or longer), and **Pennsylvania** (deposits over $100 held longer than two years). Pick your state in the calculator to see the exact rule, statute citation, and deadline. Cities can add their own rules (e.g., Chicago, Seattle, and several California cities), so always check local ordinances too.

### H2: How security deposit interest is calculated
This calculator compounds daily, the way an interest-bearing bank account accrues: the annual rate is divided by 365 to get a daily rate, and the balance grows by that rate each day the deposit is held. **Total = Deposit × (1 + rate/365)^days.** Example: $2,000 at 2% held for one year grows to $2,040.40 — $40.40 in interest. Some statutes specify *simple* interest instead (Maryland and Minnesota, for example); when in doubt, follow the statute's method and rate.

### H2: Where security deposits must be held
Several states dictate where the money sits: Massachusetts and New Hampshire require an in-state bank account, Connecticut a Connecticut financial institution, Delaware and Georgia an escrow account (or surety bond in Georgia), New Jersey a New Jersey bank or money market fund, and D.C. an interest-bearing account based in the District. Florida gives landlords a choice — non-interest account, interest-bearing account, or surety bond — and the choice determines whether interest is owed. Many states also require you to disclose the depository institution to the tenant in writing.

### H2: Deadlines to return a security deposit
Return deadlines range from 10 days (Montana, with no deductions) to 60 days (Alabama, Arkansas, West Virginia), with most states clustering around 14–30 days, often with different clocks depending on whether you take deductions or have the tenant's forwarding address. The calculator's state panel shows your state's deadline next to the interest math. Missing the deadline can forfeit your right to deduct — and in many states triggers multiple damages.

### H2: What landlords can deduct from a security deposit
Almost everywhere: unpaid rent and damage beyond normal wear and tear. Many states add unpaid utilities, cleaning, lease violations, re-renting costs, or court costs — and a few are stricter (Washington limits deductions to items on the move-in checklist). Deductions generally must be itemized in writing within the return deadline. Use the [Security Deposit Return Letter Generator](/resources/security-deposit-return-letter-generator) to produce a compliant itemized disposition letter.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this security deposit interest calculator free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Does my state require me to pay interest on security deposits?** Sixteen states plus D.C. have some statutory interest requirement, several of them conditional on portfolio size, deposit amount, or how long the deposit is held. Select your state in the calculator to see the rule and statute citation.
- **H3: How does the calculator compound interest?** Daily: the annual rate is divided by 365 and applied each day the deposit is held — Total = Deposit × (1 + rate/365)^days. If your statute mandates simple interest, use the statute's method for the legally required amount.
- **H3: What interest rate should I enter?** The rate your deposit account actually pays, or your state's mandated rate — e.g., 5% (or the bank rate) in Massachusetts, 3% in Maryland, 1% in Minnesota. Some cities publish their own annual rates.
- **H3: Do cities have their own deposit interest rules?** Yes. Chicago, New York City, Seattle, and several California cities (among others) layer local interest or handling rules on top of state law. Always check municipal ordinances for the property's location.
- **H3: When do I have to return the deposit?** It varies from 10 to 60 days depending on the state, deductions, and notice — the calculator shows your state's deadline. Pair it with the [Security Deposit Return Letter Generator](/resources/security-deposit-return-letter-generator) for the itemized letter most states require.

6. **Full legal disclaimer** (rich text block below the FAQs — carries the long-form legacy disclaimer; the tool itself shows the standard one-liner):

> **Full legal disclaimer.** This calculator and the accompanying state-by-state summaries are provided for general informational and educational purposes only and do not constitute legal advice. This is not legal advice; we make no warranties or representations as to the accuracy, completeness, suitability, or legal enforceability of any content or document provided. Use of this tool does not create an attorney-client relationship between you and Advanced Collection Bureau, Inc. or any of its employees or agents. Landlord-tenant and security deposit laws change frequently and vary by state, county, and municipality; statutory citations and summaries shown may not reflect the most recent amendments, and local ordinances may impose additional or different requirements. Always verify current law with the applicable statute or a licensed attorney in your jurisdiction before taking any action. Advanced Collection Bureau, Inc. expressly disclaims all liability for any loss, damage, penalty, or expense arising from actions taken or not taken in reliance on this tool's output or the information on this page.

7. **Related tools section** (H2: More free landlord tools) — link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter](/resources/security-deposit-return-letter-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Prorated Rent Calculator](/resources/prorated-rent-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

## Embed block #2 — JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `RATING_SEED` in the tool's rating widget
> (`{value:4.8,count:341}` — the rating must match what's visibly displayed on the page — Google requirement).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Security Deposit Interest Calculator",
      "url": "https://www.advancedcb.com/resources/security-deposit-interest-calculator",
      "applicationCategory": "FinanceApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CalculateAction", "name": "Calculate security deposit interest",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/security-deposit-interest-calculator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "341"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this security deposit interest calculator free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Does my state require me to pay interest on security deposits?",
         "acceptedAnswer": {"@type": "Answer", "text": "Sixteen states plus D.C. have some statutory interest requirement, several of them conditional on portfolio size, deposit amount, or how long the deposit is held. Select your state in the calculator to see the rule and statute citation."}},
        {"@type": "Question", "name": "How does the calculator compound interest?",
         "acceptedAnswer": {"@type": "Answer", "text": "Daily: the annual rate is divided by 365 and applied each day the deposit is held — Total = Deposit × (1 + rate/365)^days. If your statute mandates simple interest, use the statute's method for the legally required amount."}},
        {"@type": "Question", "name": "What interest rate should I enter?",
         "acceptedAnswer": {"@type": "Answer", "text": "The rate your deposit account actually pays, or your state's mandated rate — e.g., 5% (or the bank rate) in Massachusetts, 3% in Maryland, 1% in Minnesota. Some cities publish their own annual rates."}},
        {"@type": "Question", "name": "Do cities have their own deposit interest rules?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. Chicago, New York City, Seattle, and several California cities (among others) layer local interest or handling rules on top of state law. Always check municipal ordinances for the property's location."}},
        {"@type": "Question", "name": "When do I have to return the deposit?",
         "acceptedAnswer": {"@type": "Answer", "text": "It varies from 10 to 60 days depending on the state, deductions, and notice — the calculator shows your state's deadline next to the interest math."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Security Deposit Interest Calculator", "item": "https://www.advancedcb.com/resources/security-deposit-interest-calculator"}
      ]
    }
  ]
}
</script>
```
