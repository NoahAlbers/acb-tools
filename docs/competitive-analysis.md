# Competitive analysis & persona-driven upgrades (v2 pass)

How each tool stacks up against the best alternatives, who actually uses it, and what we
added to make ours the one worth bookmarking. (Competitor sites block automated fetching;
assessments are from product knowledge of these tools and their public pages.)

## Cross-cutting findings

**What the best tools get right** (calculator.net, NerdWallet, eForms): instant results, no
gates, permalink-able scenarios, and content depth around the tool. **What everyone gets
wrong:** landlord-specific tools (LandlordStudio, Mynd, Stessa, Baselane) gate results behind
email capture or product signup, have no way to *save or share* a scenario, and treat the tool
as a lead form with a calculator attached.

**The single biggest gap we can own: shareable scenarios.** A real user analyzing a deal sends
it to a partner/spouse/lender; a PM sends numbers to an owner. Almost no landlord tool supports
this. → Every calculator now encodes its inputs in a `#acb=` URL with a one-click
**"Copy link to this scenario"** button; links open the tool with the exact same numbers
(works through the Webflow iframe — the embed snippet forwards the page hash). Combined with
input persistence (already shipped), this is what makes the tools bookmarkable and shareable.

**Second gap: recurring-use documents.** Calculators are episodic; *notices* are monthly.
The v2 pass adds a Notices suite (late rent, deposit return, rent increase) — the documents
landlords need on a schedule, which is what makes the site a recurring destination. They're
also the strongest possible funnel for ACB: late rent is literally the top of the collections
funnel.

## Per-tool

### Rental Property ROI Calculator
- **Best out there:** calculator.net (depth, permalinks) — but dense, jargon-heavy, no guidance;
  BiggerPockets calculators (great reports) — but paywalled after 5 uses.
- **Personas:** (a) first-time investor evaluating one listing — needs plain English and a
  verdict; (b) active investor comparing multiple deals — needs side-by-side comparison;
  (c) agent/lender sharing analysis with a client — needs a clean shareable artifact.
- **v2 adds:** **Save & compare scenarios** (name a deal, save it, A/B compare table — beats
  BiggerPockets' paywalled feature), **one-click stress test** (vacancy ×2, rate +1%, rent −10%:
  does the deal survive? No mainstream tool does this), shareable links, print report.

### Mortgage Calculator
- **Best:** NerdWallet/Bankrate (polish) — but consumer-focused, ad-stuffed, no landlord angle.
- **Personas:** investor pre-qualifying a purchase (rate shopping across lenders); owner
  considering extra payments.
- **v2 adds:** **rate-shopping sensitivity table** (payment & total interest at ±1% in 0.25%
  steps — answers "what does an eighth save me?" instantly), shareable links. Already had:
  PMI auto-drop, extra-payment comparison, rent-coverage check (unique among mortgage tools).

### Cap Rate Calculator
- **Best:** Mynd/Omni — single formula, no context or reverse modes.
- **Personas:** buyer screening listings (solve cap), buyer with a target return (solve price —
  negotiation anchor), seller pricing a property (solve NOI).
- **v2 adds:** shareable links. Already differentiated: 3 solve modes, NOI helper, sensitivity
  matrix, interpretation chips.

### NOI Calculator
- **Best:** LandlordStudio — one rent field, lump expenses, email-gated PDF.
- **Personas:** owner prepping for a sale/refi (needs a defensible itemized NOI to hand to a
  broker/appraiser); investor verifying a seller's pro-forma.
- **v2 adds:** **CSV export** of the itemized statement (drops straight into Excel/email to a
  broker — the artifact this persona actually needs), shareable links.

### Turnover Cost Estimator
- **Competition:** none interactive (just blog posts with averages). Category is ours to own.
- **Personas:** landlord deciding whether to grant a renewal concession (retention math);
  PM justifying renewal incentives to an owner; **portfolio operator** quantifying annual
  turnover drag.
- **v2 adds:** **Portfolio mode** (units × annual turnover rate → yearly cost of turnover across
  the portfolio — the number a PM puts in an owner deck), shareable links.

### 70% Rule Calculator
- **Best:** LandlordStudio/REtipster — bare formula.
- **Personas:** wholesaler running MAO on many properties fast; flipper sanity-checking an offer.
- **v2 adds:** shareable links (wholesalers share MAO breakdowns with partners constantly).
  Already differentiated: deal-check verdicts, waterfall, sensitivity.

### Lease Agreement Generator
- **Best:** LawDepot (excellent wizard, $$ paywall at download), eForms (state pages + ratings,
  upsell-heavy). We're already the only genuinely-free state-aware builder with fillable PDFs.
- **v2 adds:** **clause preset library** in the custom-clauses step (the 12 clauses landlords
  most often go hunting for: HVAC filters, lawn care, HOA rules, pools/trampolines, guests'
  vehicles, home business, smart locks, periodic inspections, joint utilities, keys/lockouts,
  mounting TVs, satellite dishes) — one tap to insert, then editable.
- **Future (documented, not built):** per-state SEO landing pages ("Texas lease agreement"),
  Spanish translation, e-sign integration.

### Rental Application Generator
- **Best:** Zillow/Avail (force tenants into their platform), eForms (static PDF).
- Already differentiated: customizable sections, state fee caps, fair-chance warnings, fillable
  PDF. No changes this pass beyond related-links.

## New tools built this pass (v2)

| Tool | Why | Competitor gap |
|---|---|---|
| **Late Rent Notice Generator** | "Late rent notice template" + "[state] pay or quit" = huge recurring search; the exact moment a landlord is closest to needing ACB | eForms/LegalTemplates sell static PDFs; none compute the state cure period and deadline date for you |
| **Security Deposit Return Letter** | Legally required in most states, deadline-driven, high anxiety | Plenty of articles, no good interactive generator with state deadlines + itemization + "balance owed" path (which flows to collections) |
| **Rent Increase Notice Generator** | Recurring annual need; rent-control states make it scary | Static templates everywhere; none validate notice period or warn about CA/OR/WA-style caps |

Slugs: `late-rent-notice-generator`, `security-deposit-return-letter-generator`,
`rent-increase-notice-generator` — all follow the document-builder pattern (live preview,
print/PDF, state data, ACB CTA).
