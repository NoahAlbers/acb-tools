# Webflow page kit — Late Rent Notice Generator

Target URL: `https://www.advancedcb.com/resources/late-rent-notice-generator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Late Rent Notice Template — Notice to Pay or Quit Generator | Advanced Collection Bureau
- **Meta description:** Generate a free late rent notice in minutes — a friendly payment reminder or a formal Notice to Pay or Quit with your state's cure period and the deadline date computed for you. Print or save as PDF. No signup, no email.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Free Late Rent Notice Generator (Pay or Quit)
2. Intro paragraph (below H1):
   > Rent didn't arrive? Build the right notice in minutes. Choose a warm friendly reminder for a usually-reliable tenant, or a formal Notice to Pay or Quit with an itemized balance, your state's cure period, the computed deadline date, and a Certificate of Service block. Live preview as you type — then print it, save it as a PDF, or copy the text. 100% free, no signup, no email wall.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" title="Late Rent Notice Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame');
  /* forward #acb=… links into the tool */
  f.src='https://YOUR-TOOLS-HOST/tools/late-rent-notice-generator/'+(location.hash||'');
  window.addEventListener('message',function(e){
    if(e.data&&e.data.acbTool==='late-rent-notice-generator'&&e.data.height){
      f.style.height=(e.data.height+2)+'px';
    }
  });
})();
</script>
```

(Replace `YOUR-TOOLS-HOST` with the deployed host — see repo README for GitHub Pages setup. Note: this tool intentionally has no share-link feature — notices contain tenants' personal information — so the hash forwarding is simply unused.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What to include in a late rent notice
A late rent notice that holds up needs: the tenant's full name(s) and the property address; the date rent was due and the date the notice is served; an itemized breakdown of what's owed — rent, late fees the lease actually allows, returned-payment fees — minus any partial payments received; a clear total amount due; exactly how and where to pay; and, for a formal notice, the statutory demand to pay within your state's cure period or surrender possession, plus a Certificate of Service recording how and when the notice was delivered. The generator assembles all of it from a short form and computes the deadline date for you. One thing to skip: threats or amounts your lease doesn't support — they weaken your position if the case ends up in front of a judge.

### H2: Friendly reminder vs. Notice to Pay or Quit — which to send
If rent is a few days late from a tenant who normally pays, start with a friendly reminder: it preserves the relationship, collects most late rent on its own, and includes the graceful "if you've already sent payment, please disregard" line. A formal **Notice to Pay or Quit** is the legal escalation — a statutory demand that starts the clock on your state's cure period and is usually a required first step before filing an eviction for nonpayment. Many landlords send the friendly version the week rent goes late and the formal version once the lease grace period has clearly passed. The generator builds both from the same information, so switching takes one click.

### H2: State cure periods explained
The "cure period" is how long state law gives a tenant to pay (or move out) after a pay-or-quit notice is served — and it ranges from **3 days to 30 days depending on the state**. Short-fuse states like Texas, Florida, and California use 3-day notices (Florida and California count business/court days, so weekends — and in California judicial holidays — don't count). Mid-range states like Arizona, Virginia, and Illinois use 5 days; Kentucky and Michigan 7; Colorado, Maryland, and North Carolina 10. Tenant-protective states like Massachusetts, New York, and Washington require 14 days, and the District of Columbia requires 30. A few states (Georgia, Missouri, West Virginia) set no fixed statutory period, and Oregon counts in hours (72-hour and 144-hour notices). Select your state in the generator to see its period and a computed deadline date — and always verify current law before serving, because cure periods change and some cities layer on extra requirements.

### H2: How to serve a late rent notice properly
Service method matters as much as the notice itself — using the wrong one can restart the clock or get an eviction case dismissed. Most states accept one or more of: **hand delivery** to the tenant (the gold standard); **posting on the door plus mailing a copy** (often allowed only after attempting personal delivery); and **certified mail with return receipt**, which some states require and others treat as adding days to the deadline. Check your lease too — many leases specify a notice method, and you must follow it. Whatever you choose, document it: the generator includes a Certificate of Service block where the person serving the notice records the method, date, and signature, plus take a timestamped photo if you post it. Verify your state's accepted methods before serving.

### H2: What happens after the deadline — eviction and collections
If the tenant pays within the cure period, the matter ends — accept the payment and keep the paper trail. If they don't, the notice becomes your evidence: the next step is filing an eviction (unlawful detainer) case in your local court, where the properly served notice and its deadline are usually the first things the judge checks. Winning gets you possession back — but most eviction judgments don't get the money back, because the tenant has already moved on. That's where collections comes in: a collection agency that specializes in rental debt can locate the former tenant, report the debt, and recover unpaid rent, fees, and damages. Advanced Collection Bureau works on contingency — no recovery, no fee — so there's no cost to placing the account.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this late rent notice template really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers, and nothing you type leaves your browser.
- **H3: Do I have to send a notice before filing an eviction?** In nearly every state, yes — a properly served pay-or-quit (or equivalent demand) notice is a prerequisite to an eviction filing for nonpayment, and courts dismiss cases over defective notices. A few states (like New Jersey and West Virginia) handle nonpayment differently. Verify your state's current requirements before filing.
- **H3: Can I email or text the late rent notice?** A friendly reminder, sure. A formal Notice to Pay or Quit usually can't be served by email or text alone — most states require hand delivery, post-and-mail, or certified mail, unless your lease and state law expressly allow electronic service. Send the email as a courtesy copy, not as service.
- **H3: Can I include late fees in the notice?** Only fees your lease actually authorizes, and within any state cap. Some states also limit whether a pay-or-quit notice can demand fees on top of rent — when in doubt, demand the rent and bill the fees separately. The generator itemizes each charge so the total is transparent.
- **H3: What if the tenant pays part of the balance?** Be careful — in some states accepting partial payment after serving a pay-or-quit notice waives the notice and you must re-serve. The generated formal notice includes a reservation-of-rights paragraph, but check your state's rule before taking partial payment, and log it as a "payment received" credit if you re-issue.
- **H3: What if the tenant moves out still owing rent?** That's exactly what Advanced Collection Bureau does. Once the tenant is gone, send the file — ledger, lease, notices — to ACB. We've recovered over $85 million in unpaid rent, fees, and damages for landlords and property managers, on contingency: no recovery, no fee.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Security Deposit Return Letter Generator](/resources/security-deposit-return-letter-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

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
      "name": "Late Rent Notice Generator",
      "url": "https://www.advancedcb.com/resources/late-rent-notice-generator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.9", "ratingCount": "391"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this late rent notice template really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers, and nothing you type leaves your browser."}},
        {"@type": "Question", "name": "Do I have to send a notice before filing an eviction?",
         "acceptedAnswer": {"@type": "Answer", "text": "In nearly every state, yes — a properly served pay-or-quit (or equivalent demand) notice is a prerequisite to an eviction filing for nonpayment, and courts dismiss cases over defective notices. A few states handle nonpayment differently. Verify your state's current requirements before filing."}},
        {"@type": "Question", "name": "Can I email or text the late rent notice?",
         "acceptedAnswer": {"@type": "Answer", "text": "A friendly reminder, sure. A formal Notice to Pay or Quit usually can't be served by email or text alone — most states require hand delivery, post-and-mail, or certified mail, unless your lease and state law expressly allow electronic service. Send the email as a courtesy copy, not as service."}},
        {"@type": "Question", "name": "Can I include late fees in the notice?",
         "acceptedAnswer": {"@type": "Answer", "text": "Only fees your lease actually authorizes, and within any state cap. Some states also limit whether a pay-or-quit notice can demand fees on top of rent — when in doubt, demand the rent and bill the fees separately. The generator itemizes each charge so the total is transparent."}},
        {"@type": "Question", "name": "What if the tenant pays part of the balance?",
         "acceptedAnswer": {"@type": "Answer", "text": "Be careful — in some states accepting partial payment after serving a pay-or-quit notice waives the notice and you must re-serve. The generated formal notice includes a reservation-of-rights paragraph, but check your state's rule before taking partial payment."}},
        {"@type": "Question", "name": "What if the tenant moves out still owing rent?",
         "acceptedAnswer": {"@type": "Answer", "text": "That's exactly what Advanced Collection Bureau does. Once the tenant is gone, send the file — ledger, lease, notices — to ACB. We've recovered over $85 million in unpaid rent, fees, and damages for landlords and property managers, on contingency: no recovery, no fee."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Late Rent Notice Generator", "item": "https://www.advancedcb.com/resources/late-rent-notice-generator"}
      ]
    }
  ]
}
</script>
```
