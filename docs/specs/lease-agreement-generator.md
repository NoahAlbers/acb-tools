# Spec — Lease Agreement Template Generator

Slug: `lease-agreement-generator` · Benchmarks: lawdepot.com (paywalled at download, great
questionnaire UX), eforms.com (free-ish, state pages, star ratings). We win by being genuinely
100% free with no account, state-aware for all 50 states + DC, with both a guided builder and an
instant blank fillable PDF.

## Entry screen (two paths)
1. **Build my lease** → step-by-step wizard (primary CTA)
2. **Download a blank template** → state select → fillable PDF (pdf-lib) or print blanks

## Wizard steps (progress bar, back/forward, Enter to advance, answers persisted)
1. **State** — searchable select; immediately shows a "What [State] requires" panel
   (deposit limit, return deadline, entry notice, late fee rules, required disclosures).
2. **Property** — address, unit, type (house/apartment/condo/duplex/room/other), furnished?,
   included furnishings/appliances list (chips), parking, storage.
3. **Parties** — landlord name/entity + notice address, tenant names (add multiple), occupants
   (non-signing, e.g. minors), max occupancy.
4. **Term** — fixed term (start/end, auto-suggest 12 months) or month-to-month (start +
   state-appropriate termination notice auto-filled).
5. **Rent** — monthly amount, due day (default 1st), payment methods (chips), first payment
   proration (auto-calc if mid-month start), grace period & late fee (pre-filled with state cap;
   warning if user exceeds state limit), returned-check fee (state cap where applicable).
6. **Deposits** — security deposit (warn when over state max), pet deposit/fee/rent,
   last month's rent upfront?, deposit return deadline auto-noted from state.
7. **Utilities & services** — matrix of who pays (landlord/tenant): electric, gas, water/sewer,
   trash, internet, lawn, snow, pest.
8. **Policies** — pets (allowed? types/limits), smoking, subletting, alterations, renters
   insurance required (+ minimum liability), quiet hours, early termination clause option.
9. **Disclosures** — auto-checked required items by state + federal (lead paint pre-1978 toggle
   based on build year question), plus optional (mold, bed bugs, etc.). Brief explanation each.
10. **Extras** — additional custom clauses (free text, add multiple), additional terms presets.
11. **Review** — accordion summary of every answer with edit links → Generate.

## Output
- Full formatted lease in-page (professional document typography, numbered sections),
  print stylesheet → "Print / Save as PDF" (primary path).
- "Download .doc" (HTML-based .doc blob — opens in Word) and "Copy text".
- Signature blocks for all parties + date lines; lead-paint EPA pamphlet acknowledgment when
  applicable.

## State data (all 50 + DC), per state:
- `depositMax` (text, e.g. "2 months' rent"), `depositReturn` (e.g. "30 days"),
- `entryNotice` (e.g. "24 hours"), `lateFee` (cap/grace text), `nsf` (returned check fee cap text),
- `mtmNotice` (month-to-month termination notice),
- `disclosures`: array of {id, title, body} state-required disclosure clauses,
- `notes`: anything notable (e.g. CA interest on deposits in some cities).
Be accurate per training knowledge, written conservatively, and the tool must display:
"Laws current as of 2025 — verify with your state statute or attorney" in the state panel and
in the generated document footer. NOT LEGAL ADVICE disclaimer prominent.

## Lease document sections (numbered)
Parties; Property; Term; Rent; Late Charges & NSF; Security Deposit; Occupants & Use;
Utilities & Services; Maintenance & Repairs; Landlord's Right of Entry; Pets; Smoking;
Assignment & Subletting; Alterations; Renters Insurance; Rules & Regulations; Early Termination
(if chosen); Default & Remedies; Abandonment; Notices; Disclosures (state+federal);
Additional Terms; Governing Law; Entire Agreement; Signatures.

## Blank fillable PDF (pdf-lib via unpkg)
Generate a 4–6 page generic-but-state-stamped lease with AcroForm text fields/checkboxes for all
key blanks (parties, property, dates, rent, deposit, utilities checkboxes, signatures). Header
carries the state name + state quick-facts box. Filename: `Lease-Agreement-Template-[ST].pdf`.
