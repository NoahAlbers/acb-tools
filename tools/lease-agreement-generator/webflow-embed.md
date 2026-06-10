# Webflow page kit — Lease Agreement Generator

Target URL: `https://www.advancedcb.com/resources/lease-agreement-generator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Lease Agreement Generator — All 50 States | Advanced Collection Bureau
- **Meta description:** Build a state-specific residential lease in minutes — deposit limits, late-fee rules, and required disclosures handled automatically. Or download a free fillable PDF template. No signup, 100% free.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Free Residential Lease Agreement Generator
2. Intro paragraph (below H1):
   > Create a professional, state-specific residential lease agreement in about five minutes — completely free, no account, no paywall at the end. The builder automatically applies your state's security deposit limits, late-fee rules, entry notice periods, and required disclosures for all 50 states and Washington, D.C. In a hurry? Download a blank, fillable PDF template instead.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" src="https://noahalbers.github.io/acb-tools/tools/lease-agreement-generator/"
  title="Lease Agreement Generator" style="width:1px;min-width:100%;border:0;height:1200px"
  loading="eager"></iframe>
<script>
window.addEventListener('message',function(e){
  if(e.data&&e.data.acbTool==='lease-agreement-generator'){
    var f=document.getElementById('acb-tool-frame');
    if(f) f.style.height=(e.data.height+2)+'px';
  }
});
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool):

### H2: What makes a lease agreement legally solid?
A residential lease needs four things to do its job: correctly named parties and property, clear money terms (rent, deposit, fees) that stay inside your state's limits, the disclosures your state and federal law require, and signatures from every adult tenant. Most disputes trace back to vague leases — a specific, state-compliant lease is the cheapest legal protection a landlord can buy.

### H2: State laws change what your lease can say
Security deposit caps, deposit return deadlines, late-fee limits, grace periods, entry notice, and month-to-month termination notice all vary by state — and a lease term that violates them is typically unenforceable (and in some states, penalized). This generator pre-fills each rule for your state and warns you if an entry exceeds a known limit.

### H2: Required disclosures, handled
Federal law requires a lead-based paint disclosure and the EPA pamphlet for pre-1978 housing. States add their own — radon notices in Florida, Illinois, Maine, and Colorado; Megan's Law and bed bug notices in California; flood disclosures in New York, New Jersey, Texas-style addenda, and more. The builder locks required disclosures on and offers smart optional ones (mold, bed bugs, smoke/CO alarm acknowledgments).

### H2: Fixed-term vs. month-to-month
A fixed term locks in rent and occupancy for a set period — best for stability. Month-to-month offers flexibility but can end on short notice (anywhere from 7 days in North Carolina to 90 days in parts of the Northeast and West, depending on tenancy length). The generator writes your state's notice rule directly into the lease.

### H2: What to do after the lease is signed
Collect the deposit and first month's rent before handing over keys, complete a move-in checklist with photos (use our free [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator)), and store the signed lease where you can find it. If a tenant later leaves owing rent or damages beyond the deposit, that signed lease is exactly what makes the debt collectible.

5. **FAQ section** (H2: Frequently Asked Questions):

- **H3: Is this lease agreement generator really free?** Yes — build, print, and download with no account, no email wall, and no payment step. It's part of Advanced Collection Bureau's free toolkit for landlords.
- **H3: Is a lease from this generator legally binding?** A lease becomes binding when signed by the landlord and tenants. This tool produces a professional template tailored to commonly cited state rules, but it isn't legal advice — have a local attorney review it, especially for rent-controlled cities or unusual situations.
- **H3: Which states does it support?** All 50 states plus Washington, D.C., including state-specific deposit limits, return deadlines, entry notice, late-fee rules, month-to-month notice periods, and required disclosures.
- **H3: Can I download a blank lease template instead?** Yes — choose "Download a Blank Template," pick your state, and you'll get a fillable PDF you can complete on a computer or by hand. A Word (.doc) export of your custom lease is also available.
- **H3: Do I need a lead paint disclosure?** Only for housing built before 1978. Federal law then requires the disclosure plus the EPA pamphlet "Protect Your Family From Lead in Your Home." The generator includes it automatically when you indicate a pre-1978 building.
- **H3: What happens if a tenant breaks the lease and owes money?** Apply the security deposit first, following your state's itemization deadline. For anything beyond the deposit, a collection agency that specializes in rental debt — like Advanced Collection Bureau — can pursue it on contingency: no recovery, no fee.

6. **Related tools section** (H2: More free landlord tools):
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter](/resources/security-deposit-return-letter-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
   [Move-In/Move-Out Checklist](/resources/move-in-move-out-checklist-creator) ·
   [Prorated Rent Calculator](/resources/prorated-rent-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Security Deposit Interest Calculator](/resources/security-deposit-interest-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

## Embed block #2 — JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `RATING_SEED` in the tool's rating widget.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Lease Agreement Generator",
      "url": "https://www.advancedcb.com/resources/lease-agreement-generator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.9", "ratingCount": "784"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this lease agreement generator really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — build, print, and download with no account, no email wall, and no payment step. It's part of Advanced Collection Bureau's free toolkit for landlords."}},
        {"@type": "Question", "name": "Is a lease from this generator legally binding?",
         "acceptedAnswer": {"@type": "Answer", "text": "A lease becomes binding when signed by the landlord and tenants. This tool produces a professional template tailored to commonly cited state rules, but it isn't legal advice — have a local attorney review it."}},
        {"@type": "Question", "name": "Which states does it support?",
         "acceptedAnswer": {"@type": "Answer", "text": "All 50 states plus Washington, D.C., including state-specific deposit limits, return deadlines, entry notice, late-fee rules, month-to-month notice periods, and required disclosures."}},
        {"@type": "Question", "name": "Can I download a blank lease template instead?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — choose Download a Blank Template, pick your state, and you'll get a fillable PDF you can complete on a computer or by hand. A Word (.doc) export of your custom lease is also available."}},
        {"@type": "Question", "name": "Do I need a lead paint disclosure?",
         "acceptedAnswer": {"@type": "Answer", "text": "Only for housing built before 1978. Federal law then requires the disclosure plus the EPA pamphlet Protect Your Family From Lead in Your Home. The generator includes it automatically."}},
        {"@type": "Question", "name": "What happens if a tenant breaks the lease and owes money?",
         "acceptedAnswer": {"@type": "Answer", "text": "Apply the security deposit first, following your state's itemization deadline. For anything beyond the deposit, a collection agency that specializes in rental debt — like Advanced Collection Bureau — can pursue it on contingency: no recovery, no fee."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Lease Agreement Generator", "item": "https://www.advancedcb.com/resources/lease-agreement-generator"}
      ]
    }
  ]
}
</script>
```
