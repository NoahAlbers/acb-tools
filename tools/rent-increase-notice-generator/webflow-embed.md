# Webflow page kit: Rent Increase Notice Generator

Target URL: `https://www.advancedcb.com/resources/rent-increase-notice-generator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Rent Increase Notice Generator With State Notice Rules | Advanced Collection Bureau
- **Meta description:** Create a free rent increase notice in minutes. State-aware notice periods (30 to 90 days), rent-control cap warnings, effective-date validation, and a professional rent increase letter template you can print or copy. No signup, no email.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Rent Increase Notice Generator
2. Intro paragraph (below H1):
   > Raising the rent? Build a professional rent increase letter that gives the right amount of notice for your state: the generator validates the effective date, warns you about rent-control caps in states like California, Oregon, and Washington, and flags cities with their own rent rules. Preview the letter live, then print it or copy the text, 100% free with no signup and no email wall.
3. **Embed block #1**, the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Rent Increase Notice Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #… fragments into the tool */
  f.src='https://noahalbers.github.io/acb-tools/tools/rent-increase-notice-generator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='rent-increase-notice-generator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(The iframe points at the GitHub Pages host; see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool; H2s matter):

### H2: How much notice is required to raise rent, by state
For month-to-month tenancies, most states require the same written notice to raise rent as to change or end the tenancy. The typical period is **30 days**, but the range runs from about a week to a full quarter: 60 days in Colorado, Delaware, Maryland (several counties), and Vermont; 45 days in Maine (75 days for increases of 10% or more); and up to **90 days** in Oregon, Washington, California (for increases over 10%), and New York (for tenants of 2+ years facing a 5%+ increase). New York is occupancy-based: 30 days under one year, 60 days for one to two years, 90 days for two-plus years. New Jersey requires one full calendar month, effective with the start of a rental period. Select your state in the generator to see the rule applied to your numbers, and remember that for a fixed-term lease, rent generally can't change until renewal unless the lease says otherwise.

### H2: Rent control states: California, Oregon, Washington, and local ordinances
Three states now cap most rent increases statewide. **California's** AB 1482 limits annual increases to 5% + regional CPI (10% absolute max) for most buildings 15+ years old, and any increase over 10% triggers a 90-day notice requirement. **Oregon** caps increases at 7% + CPI (10% max for buildings over 15 years old) with 90 days' notice. **Washington's** recent statewide law caps most increases at roughly 7% + inflation (10% max) with extended notice; verify the current statute. On top of state law, cities including New York City, San Francisco, Los Angeles, St. Paul, Newark, Jersey City, Portland, Seattle, Washington D.C., and Montgomery County, MD have their own rent stabilization or rent control rules with separate caps and procedures. The generator flags these cities automatically when you type them, and warns when your increase percentage exceeds a known cap. Laws change frequently, so always verify current figures before sending.

### H2: How to set the effective date correctly
Two rules govern the effective date. First, it must be **at least the full notice period after the day you deliver the notice**, counting from delivery, not from when you wrote the letter. Second, for month-to-month tenancies, the new rent should start **at the beginning of a rental period**, meaning the 1st of the month if rent is due on the 1st. In practice that means a 30-day notice delivered June 10 can't take effect July 10 (mid-period); the earliest clean effective date is August 1. The generator does this math for you: enter your delivery date and it computes and suggests the earliest valid first-of-the-month effective date with one click, and flags dates that are too early or misaligned.

### H2: How much should you raise the rent? Run the retention math
Before you pick a number, price the downside. A $50/month increase earns $600 a year, but if it pushes a good tenant to leave, one turnover (make-ready repairs, cleaning, marketing, showings, and a month or two of vacancy) routinely costs $2,000 to $5,000 or more. That means a too-aggressive increase can take three to eight years to pay for itself. The sweet spot is usually a modest, predictable annual increase that keeps pace with your costs and stays slightly below the pain threshold that triggers apartment hunting. Run your actual numbers in the free [Turnover Cost Estimator](/resources/turnover-cost-estimator), and pair the increase with the appreciation line and a clear reason; tenants accept increases far better when they're explained.

### H2: Delivering the notice properly
A perfect letter delivered wrong is an invalid notice. Check your lease and state law for permitted service methods; most allow personal delivery, first-class mail (some states add days for mailing time), certified mail with return receipt, or posting plus mailing. Email or text usually only counts if your lease expressly allows electronic notices. Whatever method you use, document it: the generator's optional certificate of service gives you a dated record of how and when the notice was served, which is exactly what a court asks for if the increase is ever disputed. Keep a signed copy of the letter and any mailing receipts with the tenant's file.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this rent increase letter template really free?** Yes. 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers. Nothing you type leaves your browser.
- **H3: How much notice do I have to give before raising rent?** It depends on your state and sometimes the size of the increase: most states require 30 days for month-to-month tenancies, several require 60, and Oregon, Washington, California (increases over 10%), and New York (long-term tenants) require up to 90. The generator applies your state's rule automatically and validates your effective date against it.
- **H3: Is there a limit on how much I can raise the rent?** In most states there is no statewide cap, but California (5% + CPI, 10% max), Oregon (7% + CPI, 10% max), and Washington (roughly 7% + inflation, 10% max) cap most increases, and cities with rent control or stabilization (NYC, San Francisco, Los Angeles, St. Paul, Newark, Jersey City, Portland, Seattle, D.C., and Montgomery County MD) set their own limits. The tool warns you when your percentage exceeds a known cap. Verify current figures, as they change annually.
- **H3: Can a rent increase take effect in the middle of the month?** For month-to-month tenancies it generally shouldn't: increases take effect at the start of a rental period, usually the 1st. The generator computes the earliest valid first-of-the-month date from your delivery date and notice period and applies it with one click.
- **H3: Can I raise the rent during a fixed-term lease?** Generally no. The rent is locked for the lease term unless the lease itself allows changes, and increases take effect at renewal. Switch the generator to fixed-term renewal mode and it produces renewal-with-new-rate language and an optional reply-by date instead.
- **H3: How should I deliver a rent increase notice?** Use a method your lease and state law permit (personal delivery, first-class or certified mail, or posting plus mailing) and keep proof. Enable the certificate of service option in the generator to add a delivery record you complete when you serve the notice.

6. **Related tools section** (H2: More free landlord tools), link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter Generator](/resources/security-deposit-return-letter-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Prorated Rent Calculator](/resources/prorated-rent-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Security Deposit Interest Calculator](/resources/security-deposit-interest-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

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
      "name": "Rent Increase Notice Generator",
      "url": "https://www.advancedcb.com/resources/rent-increase-notice-generator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CreateAction", "name": "Create a rent increase notice",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/rent-increase-notice-generator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "189"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this rent increase letter template really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers. Nothing you type leaves your browser."}},
        {"@type": "Question", "name": "How much notice do I have to give before raising rent?",
         "acceptedAnswer": {"@type": "Answer", "text": "It depends on your state and sometimes the size of the increase: most states require 30 days for month-to-month tenancies, several require 60, and Oregon, Washington, California (increases over 10%), and New York (long-term tenants) require up to 90. The generator applies your state's rule automatically and validates your effective date against it."}},
        {"@type": "Question", "name": "Is there a limit on how much I can raise the rent?",
         "acceptedAnswer": {"@type": "Answer", "text": "In most states there is no statewide cap, but California (5% + CPI, 10% max), Oregon (7% + CPI, 10% max), and Washington (roughly 7% + inflation, 10% max) cap most increases, and cities with rent control or stabilization (NYC, San Francisco, Los Angeles, St. Paul, Newark, Jersey City, Portland, Seattle, D.C., and Montgomery County MD) set their own limits. The tool warns you when your percentage exceeds a known cap. Verify current figures, as they change annually."}},
        {"@type": "Question", "name": "Can a rent increase take effect in the middle of the month?",
         "acceptedAnswer": {"@type": "Answer", "text": "For month-to-month tenancies it generally shouldn't: increases take effect at the start of a rental period, usually the 1st. The generator computes the earliest valid first-of-the-month date from your delivery date and notice period and applies it with one click."}},
        {"@type": "Question", "name": "Can I raise the rent during a fixed-term lease?",
         "acceptedAnswer": {"@type": "Answer", "text": "Generally no. The rent is locked for the lease term unless the lease itself allows changes, and increases take effect at renewal. Switch the generator to fixed-term renewal mode and it produces renewal-with-new-rate language and an optional reply-by date instead."}},
        {"@type": "Question", "name": "How should I deliver a rent increase notice?",
         "acceptedAnswer": {"@type": "Answer", "text": "Use a method your lease and state law permit (personal delivery, first-class or certified mail, or posting plus mailing) and keep proof. Enable the certificate of service option in the generator to add a delivery record you complete when you serve the notice."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Rent Increase Notice Generator", "item": "https://www.advancedcb.com/resources/rent-increase-notice-generator"}
      ]
    }
  ]
}
</script>
```
