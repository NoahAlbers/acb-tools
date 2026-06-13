# Webflow page kit: Move-In / Move-Out Checklist Creator

Target URL: `https://www.advancedcb.com/resources/move-in-move-out-checklist-creator`

> ⚠️ **This kit REPLACES the existing 4-embed implementation on that page.** Delete all four
> legacy embed blocks (the old checklist creator shipped as four separate Webflow embeds) and
> paste the single iframe embed below in their place. Existing share links keep working, > the iframe snippet forwards the page's hash into the tool, and the tool still reads the
> legacy `#d=` link format.

## Page settings (Webflow → Page Settings)

- **Title tag:** Free Move-In Move-Out Inspection Checklist Creator | Advanced Collection Bureau
- **Meta description:** Create a room-by-room move in move out checklist with condition ratings, notes, and photos, then download a signed PDF rental inspection checklist. 100% free, no signup, no email required.
- **Open Graph title/description:** same as above.

## Page structure

1. **H1:** Move-In / Move-Out Checklist
2. Intro paragraph (below H1):
   > Document your rental's condition the right way. Walk through the unit room by room, rate every item (Good, Cosmetic damage, or Repair Required), add notes and photos, and export a professional rental inspection checklist PDF with signature lines for every tenant and the inspector. Works for move-in and move-out, completely free, no account, no email wall.
3. **Embed block #1**, the tool iframe (paste in an Embed element):

```html
<iframe id="acb-tool-frame" src="https://noahalbers.github.io/acb-tools/tools/move-in-move-out-checklist-creator/"
  title="Move-In / Move-Out Checklist Creator" style="width:1px;min-width:100%;border:0;height:1200px"
  loading="eager"></iframe>
<script>
(function(){
  /* Forward the page hash into the iframe so shared checklists open.
     This passes the WHOLE hash, so both #acb= links and legacy #d=
     links (from the old 4-embed version, already shared in the wild)
     keep working. */
  var f=document.getElementById('acb-tool-frame');
  if(f&&location.hash){f.src=f.src.split('#')[0]+location.hash;}
})();
window.addEventListener('message',function(e){
  if(e.data&&e.data.acbTool==='move-in-move-out-checklist-creator'){
    var f=document.getElementById('acb-tool-frame');
    if(f) f.style.height=(e.data.height+2)+'px';
  }
});
</script>
```

(The iframe points at the GitHub Pages host, see repo README for the Pages setup.)

4. **SEO content section** (rich text below the tool):

### H2: Why document the unit's condition at move-in?
The security deposit fight is almost always a documentation fight. A dated, signed move-in checklist establishes the unit's condition before the tenant ever unpacks, so at move-out there's no argument about whether the carpet stain or the cracked tile "was already like that." Most states put the burden on the landlord to prove damage beyond normal wear and tear, and several require condition documentation before deposit deductions will hold up. Five minutes with a checklist at move-in routinely saves hundreds of dollars and a small-claims hearing at move-out.

### H2: How to do a walk-through inspection
Do the walk-through together with the tenant when the unit is empty and clean. Go room by room, walls and ceilings, floors, lights and outlets, doors and knobs, then the room-specific items (appliances in the kitchen, the tub and exhaust fan in bathrooms, the garage door, exterior siding and gutters). Mark only what needs attention: anything not flagged is recorded as Good. Test what can be tested, run faucets, flip every switch, open every window. Finish by having every tenant and the inspector sign the same document, and give the tenant a copy.

### H2: Photos are your best evidence
Notes describe a problem; photos prove it. Attach a photo to anything you flag, a wide shot for context and a close-up of the damage, plus a few general shots of each room even when everything looks fine. This tool compresses photos automatically and embeds them in the PDF next to the item they document, so the date, the room, and the image travel together in one signed file. (Photos stay in the PDF only, share links carry the rooms, ratings, and notes without them.)

### H2: The move-out comparison and your deposit
At move-out, repeat the same walk-through with the move-in checklist in hand and compare item by item. Anything that went from Good to damaged, beyond normal wear and tear, is a documented, defensible deduction. From there, follow your state's deposit timeline: most states require an itemized statement and the remaining deposit within 14 to 60 days of move-out. Use our free [Security Deposit Return Letter Generator](/resources/security-deposit-return-letter-generator) to send a compliant itemization.

### H2: What counts as normal wear and tear?
Normal wear and tear is the gradual decline that happens no matter how careful a tenant is: faded paint, lightly worn carpet in walkways, small nail holes from hanging pictures, loose door handles. Damage is different, pet stains, burns, large holes in drywall, broken appliances, unauthorized paint colors. You can deduct for damage but not for wear and tear, and the side-by-side move-in/move-out checklists are exactly how you show which is which.

5. **FAQ section** (H2: Frequently Asked Questions):

- **H3: Is this move-in/move-out checklist really free?** Yes, build the checklist, attach photos, and download the signed-ready PDF with no account, no email wall, and no payment step. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers.
- **H3: Is a move-in checklist legally required?** Several states require landlords to document the unit's condition or provide an inventory checklist at move-in, and in many of them it's a precondition for keeping any of the security deposit. Even where it isn't required, a signed checklist is the standard evidence courts expect in deposit disputes.
- **H3: Should the tenant sign the checklist?** Yes. A checklist signed by both parties at move-in is far stronger evidence than one the landlord completed alone. This tool adds a signature and date line for every tenant you list, plus the inspector.
- **H3: Can I add photos to the checklist?** Yes, attach photos to any item and they're compressed automatically and embedded in the PDF next to that item. Photos are excluded from share links (they're too large for a URL) but always included in the PDF.
- **H3: Can I share the checklist with my tenant or property manager?** Yes, the Share button creates a link (plus a QR code, email, and text option) that opens the same checklist, rooms, ratings, and notes on this page. Links made with the previous version of this tool still work too.
- **H3: What if the tenant leaves owing more than the deposit covers?** Apply the deposit first, following your state's itemization deadline. For unpaid rent or damage beyond the deposit, a collection agency that specializes in rental debt, like Advanced Collection Bureau, can pursue it on contingency: no recovery, no fee.

6. **Related tools section** (H2: More free landlord tools):
   [Lease Agreement Generator](/resources/lease-agreement-generator) ·
   [Rental Application Generator](/resources/rental-application-generator) ·
   [Late Rent Notice Generator](/resources/late-rent-notice-generator) ·
   [Security Deposit Return Letter](/resources/security-deposit-return-letter-generator) ·
   [Rent Increase Notice Generator](/resources/rent-increase-notice-generator) ·
   [Security Deposit Interest Calculator](/resources/security-deposit-interest-calculator) ·
   [Prorated Rent Calculator](/resources/prorated-rent-calculator) ·
   [Rent Increase Calculator](/resources/rent-increase-calculator) ·
   [Rental Property ROI Calculator](/resources/rental-property-roi-calculator) ·
   [Mortgage Calculator](/resources/mortgage-calculator) ·
   [Cap Rate Calculator](/resources/cap-rate-calculator) ·
   [NOI Calculator](/resources/net-operating-income-calculator) ·
   [Turnover Cost Estimator](/resources/turnover-cost-estimator) ·
   [70% Rule Calculator](/resources/70-percent-rule-calculator)

## Embed block #2: JSON-LD (paste in page head custom code)

> ⚠️ Keep `ratingValue`/`ratingCount` in sync with the `RATING_SEED` in the tool's rating widget
> (currently 4.9 / 512).

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "WebApplication",
      "name": "Move-In / Move-Out Checklist Creator",
      "url": "https://www.advancedcb.com/resources/move-in-move-out-checklist-creator",
      "applicationCategory": "BusinessApplication",
      "operatingSystem": "Web",
      "offers": {"@type": "Offer", "price": "0", "priceCurrency": "USD"},
      "potentialAction": {"@type": "CreateAction", "name": "Create a move-in/move-out checklist",
        "target": {"@type": "EntryPoint", "urlTemplate": "https://www.advancedcb.com/resources/move-in-move-out-checklist-creator"}},
      "aggregateRating": {"@type": "AggregateRating", "ratingValue": "4.9", "ratingCount": "512"},
      "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau",
        "url": "https://www.advancedcb.com"}
    },
    {
      "@type": "FAQPage",
      "mainEntity": [
        {"@type": "Question", "name": "Is this move-in/move-out checklist really free?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes, build the checklist, attach photos, and download the signed-ready PDF with no account, no email wall, and no payment step. It's part of Advanced Collection Bureau's free toolkit for landlords and property managers."}},
        {"@type": "Question", "name": "Is a move-in checklist legally required?",
         "acceptedAnswer": {"@type": "Answer", "text": "Several states require landlords to document the unit's condition or provide an inventory checklist at move-in, and in many of them it's a precondition for keeping any of the security deposit. Even where it isn't required, a signed checklist is the standard evidence courts expect in deposit disputes."}},
        {"@type": "Question", "name": "Should the tenant sign the checklist?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes. A checklist signed by both parties at move-in is far stronger evidence than one the landlord completed alone. This tool adds a signature and date line for every tenant you list, plus the inspector."}},
        {"@type": "Question", "name": "Can I add photos to the checklist?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes, attach photos to any item and they're compressed automatically and embedded in the PDF next to that item. Photos are excluded from share links but always included in the PDF."}},
        {"@type": "Question", "name": "Can I share the checklist with my tenant or property manager?",
         "acceptedAnswer": {"@type": "Answer", "text": "Yes, the Share button creates a link (plus a QR code, email, and text option) that opens the same checklist, rooms, ratings, and notes. Links made with the previous version of this tool still work too."}},
        {"@type": "Question", "name": "What if the tenant leaves owing more than the deposit covers?",
         "acceptedAnswer": {"@type": "Answer", "text": "Apply the deposit first, following your state's itemization deadline. For unpaid rent or damage beyond the deposit, a collection agency that specializes in rental debt, like Advanced Collection Bureau, can pursue it on contingency: no recovery, no fee."}}
      ]
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Home", "item": "https://www.advancedcb.com/"},
        {"@type": "ListItem", "position": 2, "name": "Free Tools", "item": "https://www.advancedcb.com/resources"},
        {"@type": "ListItem", "position": 3, "name": "Move-In / Move-Out Checklist Creator", "item": "https://www.advancedcb.com/resources/move-in-move-out-checklist-creator"}
      ]
    }
  ]
}
</script>
```
