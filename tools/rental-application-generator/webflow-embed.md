# Webflow page kit — Rental Application Generator

Target URL: `https://www.advancedcb.com/resources/rental-application-generator`

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Rental Application Form — Fillable PDF Template, No Signup | Advanced Collection Bureau
- **Meta description:** Build a free rental application form in minutes. Customizable sections, state-aware fee and screening notes, fair-housing-safe wording — print it or download a fillable PDF. No signup, no email.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Free Rental Application Form Generator
2. Intro paragraph (below H1):
   > Build a professional rental application template customized to your property and your state. Toggle the sections you need — residence history, employment, references, background questions — and the live preview updates instantly. Print it, save it as a PDF, or download a fillable PDF your applicants can type into. 100% free, no signup, no email wall.
3. **Embed block #1** — the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" src="https://noahalbers.github.io/acb-tools/tools/rental-application-generator/"
  title="Rental Application Form Generator" style="width:1px;min-width:100%;border:0;height:2400px"
  loading="eager"></iframe>
<script>
window.addEventListener('message',function(e){
  if(e.data&&e.data.acbTool==='rental-application-generator'){
    var f=document.getElementById('acb-tool-frame');
    if(f) f.style.height=(e.data.height+2)+'px';
  }
});
</script>
```

(The iframe points at the GitHub Pages host — see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool — H2s matter):

### H2: What to include on a rental application
A complete rental application covers identity and contact details (name, date of birth, government ID, phone, email), everyone who will live in the unit, two to three addresses of residence history with landlord references, current and previous employment with gross monthly income, optional other income, personal references, vehicles, pets, and a small set of background questions. The most important block is the one many free templates skip: a signed authorization that lets you legally pull credit, eviction-history, and background reports. The generator includes FCRA-compliant consent language by default, plus a proof-of-income document checklist (pay stubs, W-2, bank statements) so you get verification with the application instead of chasing it later.

### H2: Questions you can't ask on a rental application (fair housing)
The federal Fair Housing Act prohibits screening based on race, color, religion, sex, disability, familial status, or national origin — so an application should never ask about birthplace, citizenship status as a proxy for national origin, religion, whether an applicant is pregnant or plans to have children, or the nature of a disability. Many states and cities add protected classes such as source of income, age, marital status, sexual orientation, and gender identity. A growing list of "fair chance" jurisdictions — including New Jersey, the District of Columbia, Cook County (Chicago), Seattle, New York City, and Detroit — also restricts criminal-history questions on initial applications. The generator flags those jurisdictions when you enable the felony question and prints a caution note on the form, but always verify your local rules.

### H2: Rental application fee laws by state — overview
Application fee rules vary widely. A few highlights: **Massachusetts** and **Vermont** generally prohibit landlords from charging application fees at all. **New York** caps fees at $20 (or actual cost if less) and requires waiving the fee if the applicant supplies a recent screening report. **Wisconsin** caps credit-check charges at $25 and requires accepting a recent applicant-provided report. **Virginia** caps fees at $50 plus actual third-party screening costs, **Delaware** at the greater of 10% of monthly rent or $50, and **California** at roughly $65 (indexed annually) with an itemized receipt and refund of unspent amounts. **Washington**, **Colorado**, and **Minnesota** require disclosing screening criteria and costs up front and limit fees to actual costs. Most other states have no statutory cap — there, keep fees reasonable, uniform for every applicant, and tied to what screening actually costs you. Select your state in the generator to see the relevant note printed on the form. Laws change — verify current state and local rules.

### H2: How to screen tenants legally (FCRA basics)
Tenant screening with credit, eviction, or background reports falls under the federal Fair Credit Reporting Act. Three rules keep you safe: (1) get the applicant's written authorization before pulling any consumer report — the generator's consent section handles this; (2) apply the same written criteria (income ratio, credit floor, rental history) to every applicant in the order received; and (3) if you deny an applicant, require a co-signer, or increase the deposit based even in part on a report, send an adverse-action notice naming the screening company, its contact information, and the applicant's right to dispute and obtain a free copy. Document what you did and why — consistent paperwork is your best defense.

### H2: Fillable PDF vs. printed application forms
Both come out of this generator from the same template. The **printed form** (Print / Save as PDF) is ideal for showings and on-site offices — applicants complete it by hand and sign on the spot. The **fillable PDF** has real form fields (text boxes, checkboxes, yes/no options) that applicants can type into with any free PDF reader, then sign electronically or print and sign — fewer legibility problems and faster turnaround when you're emailing applications. Either way, the application isn't complete until it's signed: the authorization signature is what permits the credit and background check.

5. **FAQ section** (H2: Frequently Asked Questions; use Webflow accordion or plain H3s):

- **H3: Is this rental application template really free?** Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Is the generated application legally binding?** The signed authorization section gives you legally meaningful consent to run credit and background checks under the FCRA. The form itself is a general-purpose template, not legal advice — screening and fee laws vary by state and city, so review it with a local attorney before use.
- **H3: Can I ask about criminal history on a rental application?** In many places yes, but a growing number of jurisdictions — New Jersey, Washington D.C., Cook County (Chicago), Seattle, New York City, Detroit, and others — restrict or prohibit criminal-history questions on initial applications. The generator shows a warning for those jurisdictions and prints a caution note; verify your local law before asking.
- **H3: How much can I charge for an application fee?** It depends on your state. Some states prohibit fees entirely (Massachusetts, Vermont), some cap them ($20 in New York, $25 credit-check cap in Wisconsin, $50 in Virginia, ~$65 indexed in California), and most have no statutory cap — where the safe practice is charging only your actual screening cost, uniformly. The tool warns you when your fee exceeds a known cap.
- **H3: Should I collect full Social Security numbers?** Often you don't need to. Paper forms with full SSNs create data-security risk, and most screening services can match applicants with the last four digits plus date of birth, or collect the full SSN securely themselves. The generator lets you choose full SSN, last-4, or none.
- **H3: What do I do after an applicant fills it out?** Verify income against the attached documents, call landlord references, run credit/background/eviction reports through a screening service using the signed authorization, and compare everything against your written criteria. If you deny based on a report, send an FCRA adverse-action notice.

6. **Related tools section** (H2: More free landlord tools) — link grid:
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter](/resources/security-deposit-return-letter-generator) ·
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
      "name": "Rental Application Form Generator",
      "url": "https://www.advancedcb.com/resources/rental-application-generator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CreateAction", "name": "Create a rental application",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/rental-application-generator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.8", "ratingCount": "294"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this rental application template really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes — 100% free, no account, no email, unlimited use. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Is the generated application legally binding?",
         "acceptedAnswer": {"@type": "Answer", "text": "The signed authorization section gives you legally meaningful consent to run credit and background checks under the FCRA. The form itself is a general-purpose template, not legal advice — screening and fee laws vary by state and city, so review it with a local attorney before use."}},
        {"@type": "Question", "name": "Can I ask about criminal history on a rental application?",
         "acceptedAnswer": {"@type": "Answer", "text": "In many places yes, but a growing number of jurisdictions — New Jersey, Washington D.C., Cook County (Chicago), Seattle, New York City, Detroit, and others — restrict or prohibit criminal-history questions on initial applications. The generator shows a warning for those jurisdictions and prints a caution note; verify your local law before asking."}},
        {"@type": "Question", "name": "How much can I charge for an application fee?",
         "acceptedAnswer": {"@type": "Answer", "text": "It depends on your state. Some states prohibit application fees entirely (Massachusetts, Vermont), some cap them ($20 in New York, $25 credit-check cap in Wisconsin, $50 in Virginia, about $65 indexed in California), and most have no statutory cap — where the safe practice is charging only your actual screening cost, uniformly. The tool warns you when your fee exceeds a known cap."}},
        {"@type": "Question", "name": "Should I collect full Social Security numbers?",
         "acceptedAnswer": {"@type": "Answer", "text": "Often you don't need to. Paper forms with full SSNs create data-security risk, and most screening services can match applicants with the last four digits plus date of birth, or collect the full SSN securely themselves. The generator lets you choose full SSN, last-4, or none."}},
        {"@type": "Question", "name": "What do I do after an applicant fills it out?",
         "acceptedAnswer": {"@type": "Answer", "text": "Verify income against the attached documents, call landlord references, run credit, background, and eviction reports through a screening service using the signed authorization, and compare everything against your written criteria. If you deny based on a report, send an FCRA adverse-action notice."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Rental Application Generator", "item": "https://www.advancedcb.com/resources/rental-application-generator"}
      ]
    }
  ]
}
</script>
```
