# Webflow page kit: Security Deposit Return Letter Generator

Target URL: `https://www.advancedcb.com/resources/security-deposit-return-letter-generator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Security Deposit Return Letter and Itemized Deduction Generator | Advanced Collection Bureau
- **Meta description:** Write a state-compliant security deposit return letter in minutes. See your state's deadline, itemize deductions that hold up, and handle full refunds, partial refunds, or balances the tenant still owes. Free, no signup.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Deposit Return Letter Generator
2. Intro paragraph (below H1):
   > Returning a security deposit the wrong way is one of the most expensive mistakes a landlord can make: miss your state's deadline or skip the itemized statement and many states award the tenant double or triple damages. This free generator builds a professional security deposit return letter (or itemized security deposit deduction letter) for any U.S. state, showing your state's return deadline with a computed send-by date, itemizing deductions with live math, and printing or saving the finished letter as a PDF. It handles full refunds, partial refunds, no-refund letters, and demand letters when the tenant owes more than the deposit, 100% free with no signup and no email wall.
3. **Embed block #1**, the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" aria-label="Security Deposit Return Letter Generator"
  style="width:1px;min-width:100%;border:0;height:2400px" loading="eager"></iframe>
<script>
(function(){
  var f=document.getElementById('acb-tool-frame'),slug='security-deposit-return-letter-generator';
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

### H2: Security deposit return deadlines by state, an overview
Every state sets its own clock, and most start it at move-out (a few start when the tenant hands over a forwarding address). Deadlines range from **14 to 60 days**: the fastest states include **Hawaii, Nebraska, New York, Vermont, and Alaska** (14 days), with **Arizona** at 14 business days and **Florida** at 15 days when there are no deductions (30 days to give notice of a claim). The big middle group (**Georgia, Texas, Massachusetts, Washington, Nevada, Ohio,** and many more) allows 30 days, **California, Minnesota, Wisconsin, and Idaho** allow 21, and the slowest states (**Indiana, Maryland, Virginia, Mississippi, Oklahoma, and Washington, D.C.**) allow 45, with **Alabama, Arkansas, and West Virginia** topping out at 60 days. Several states use split deadlines: a short one if you're returning everything and a longer one when you're claiming deductions. Select your state in the generator to see the exact rule and a send-by date computed from your tenant's move-out date. Deadlines change, so verify current law before relying on them.

### H2: What you can and can't deduct: normal wear and tear
You can generally deduct unpaid rent, unpaid utilities owed under the lease, cleaning needed to return the unit to its move-in condition, repair of damage beyond normal wear and tear, and missing keys or fixtures. You **cannot** deduct for normal wear and tear, meaning the gradual decline that happens when a tenant simply lives in a unit. Matted or lightly worn carpet, small nail holes from hanging pictures, faded paint, and minor scuffs are normal wear and are not deductible. Pet stains and carpet burns, large holes in walls or doors, broken fixtures and windows, unauthorized paint, and filth requiring deep cleaning are damage, and damage is deductible. Charging for normal wear is the #1 thing that loses deposit disputes, and judges in many states can award the tenant a multiple of the wrongly withheld amount. The generator includes this guard-rail checklist right in the builder.

### H2: How to itemize deductions so they hold up
Vague deductions lose cases. "Cleaning, $300" invites a dispute; "professional carpet cleaning to remove pet stains in both bedrooms, $285 invoice attached" wins it. For every deduction: (1) name the category (unpaid rent, cleaning beyond normal use, repairs beyond normal wear and tear, unpaid utilities, missing items); (2) describe the specific item and why it exceeds normal wear; (3) state the actual cost and attach the receipt, invoice, or written estimate (several states require receipts above a threshold); and (4) support it with your move-in/move-out inspection photos. Send the letter to the tenant's forwarding address (or their last known address if they never provided one; in several states the clock or your duty pauses until they do) and keep proof of mailing, such as a USPS Certificate of Mailing, which the generator can note on the letter.

### H2: Which states require interest on security deposits?
A handful of states require landlords to pay interest on held deposits in at least some situations: **Connecticut** requires interest on deposits; **Washington, D.C.** requires deposits to sit in an interest-bearing account with accrued interest payable to the tenant; **Massachusetts** requires annual interest (and enforces its deposit law strictly); **Maryland** owes interest on deposits of $50+ held 6+ months; **Minnesota** owes interest on deposits; **New Jersey** requires the deposit to be held in an interest-bearing N.J. account with written notice of its location; **Ohio** owes interest on deposits over one month's rent held 6+ months; and **Pennsylvania** deposits held beyond 2 years accrue interest payable to the tenant. Some cities (notably Chicago) add their own interest ordinances. The generator flags these states and gives you a field to include accrued interest in the deposit accounting. Rates and rules change, so verify the current figure before sending.

### H2: When damage exceeds the deposit: turning the letter into a demand
If unpaid rent and legitimate damage add up to more than the deposit, the deposit accounting flips: instead of a refund, the letter becomes an itemized statement plus a demand for the remaining balance with a clear pay-by date. Choose 'Tenant owes more' in the generator and it restructures the letter automatically with itemized deductions, the balance due in the accounting table, payment instructions, and notice that the account may be referred to a collection agency if unpaid. A written, itemized demand letter is also the foundation for what comes next: if the former tenant doesn't pay, a collection agency that specializes in landlord-tenant debt, like Advanced Collection Bureau, can pursue the balance on a contingency basis, so you pay nothing unless money is recovered.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this security deposit return letter template really free?** Yes. 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers, and nothing you type leaves your browser.
- **H3: How long do I have to return a security deposit?** It depends on your state: anywhere from 14 to 60 days, usually counted from move-out. Some states have split deadlines (a shorter one when there are no deductions) and a few count business days or start the clock at the forwarding address. Pick your state in the generator to see the rule and a computed send-by date, and verify current law before relying on it.
- **H3: What can I legally deduct from a security deposit?** Unpaid rent, unpaid utilities, cleaning beyond normal use, repairs for damage beyond normal wear and tear, and missing keys or items. You cannot deduct for normal wear and tear such as matted carpet, small nail holes, or faded paint. Itemize each deduction with a specific description and keep receipts; several states require them.
- **H3: What if the deductions are more than the deposit?** The letter becomes an itemized statement plus a demand for the balance with a pay-by date; the generator's 'Tenant owes more' mode builds it for you. If the former tenant doesn't pay by that date, that's exactly what Advanced Collection Bureau collects: ACB has recovered over $85 million in unpaid rent, fees, and damages for landlords and property managers, on a no-recovery, no-fee basis.
- **H3: What happens if I miss my state's deposit deadline?** In many states you forfeit the right to keep any of the deposit, and a wrongful or late withholding can expose you to double or triple damages plus attorney's fees. Send the itemized letter on time. Even if you're still finalizing repair invoices, a timely itemized statement with good-faith estimates beats a late perfect one in most states.
- **H3: Do I need to send the letter a specific way?** Several states require first-class mail, certified mail, or delivery to the tenant's forwarding address. If the tenant never gave you one, most states let you use their last known address (often the rental itself) and some pause your obligations until an address is provided. Whatever your state requires, keep proof of mailing; the generator can add a certificate-of-mailing line to the letter.

6. **Related tools section** (H2: More free landlord tools), link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
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

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `SEED` in the tool's rating widget
> (the rating must match what's visibly displayed on the page; this is a Google requirement).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Security Deposit Return Letter Generator",
      "url": "https://www.advancedcb.com/resources/security-deposit-return-letter-generator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CreateAction", "name": "Create a security deposit return letter",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/security-deposit-return-letter-generator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "227"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this security deposit return letter template really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers, and nothing you type leaves your browser."}},
        {"@type": "Question", "name": "How long do I have to return a security deposit?",
         "acceptedAnswer": {"@type": "Answer", "text": "It depends on your state: anywhere from 14 to 60 days, usually counted from move-out. Some states have split deadlines (a shorter one when there are no deductions) and a few count business days or start the clock at the forwarding address. Pick your state in the generator to see the rule and a computed send-by date, and verify current law before relying on it."}},
        {"@type": "Question", "name": "What can I legally deduct from a security deposit?",
         "acceptedAnswer": {"@type": "Answer", "text": "Unpaid rent, unpaid utilities, cleaning beyond normal use, repairs for damage beyond normal wear and tear, and missing keys or items. You cannot deduct for normal wear and tear such as matted carpet, small nail holes, or faded paint. Itemize each deduction with a specific description and keep receipts; several states require them."}},
        {"@type": "Question", "name": "What if the deductions are more than the deposit?",
         "acceptedAnswer": {"@type": "Answer", "text": "The letter becomes an itemized statement plus a demand for the balance with a pay-by date; the generator's 'Tenant owes more' mode builds it for you. If the former tenant doesn't pay by that date, that's exactly what Advanced Collection Bureau collects: ACB has recovered over $85 million in unpaid rent, fees, and damages for landlords and property managers, on a no-recovery, no-fee basis."}},
        {"@type": "Question", "name": "What happens if I miss my state's deposit deadline?",
         "acceptedAnswer": {"@type": "Answer", "text": "In many states you forfeit the right to keep any of the deposit, and a wrongful or late withholding can expose you to double or triple damages plus attorney's fees. Send the itemized letter on time. Even if you're still finalizing repair invoices, a timely itemized statement with good-faith estimates beats a late perfect one in most states."}},
        {"@type": "Question", "name": "Do I need to send the letter a specific way?",
         "acceptedAnswer": {"@type": "Answer", "text": "Several states require first-class mail, certified mail, or delivery to the tenant's forwarding address. If the tenant never gave you one, most states let you use their last known address (often the rental itself) and some pause your obligations until an address is provided. Whatever your state requires, keep proof of mailing; the generator can add a certificate-of-mailing line to the letter."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Security Deposit Return Letter Generator", "item": "https://www.advancedcb.com/resources/security-deposit-return-letter-generator"}
      ]
    }
  ]
}
</script>
```
