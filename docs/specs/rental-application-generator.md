# Spec — Rental Application Form Generator

Slug: `rental-application-generator` · Benchmarks: eforms/ezlandlordforms paid templates, Zillow
(forces their platform). We win: free, customizable sections, state-aware notes, fillable PDF +
print, fair-housing-safe defaults.

## Flow (builder, not a long wizard — single page with section toggles + a few config steps)
1. **Setup card** — Property/company name, property address, application fee ($ with state-cap
   warning where applicable), who to return the form to (email/address/phone).
2. **Sections** (toggle on/off, drag-free fixed order, each expandable to tweak options):
   - Applicant info (always on): name, DOB, SSN (toggle full/last-4/none with privacy hint),
     phone, email, gov ID, emergency contact
   - Co-applicants/occupants (count fields)
   - Residence history (configurable: last 2 or 3 addresses; landlord refs w/ phone)
   - Employment & income (current + previous employer, income, toggle: require proof docs list)
   - Other income sources
   - References (personal/professional, count)
   - Vehicles (count), Pets (count + type/weight)
   - Background questions (each individually toggleable with fair-housing notes:
     eviction history, felony conviction [show warning chip: some states/cities restrict criminal
     history questions — e.g. CA, NJ, IL localities; recommend checking local law], bankruptcy,
     smoking)
   - Authorization & consent (always on): credit/background check consent text, FCRA notice,
     signature/date
3. **State select** — adds state-specific note block (application fee caps where they exist,
   e.g. NY $20 cap; receipt requirements; criminal-history restrictions flag) into the form
   footer and shows warnings in the builder.
4. **Generate** — live preview updates as sections toggle.

## Output
- Print-ready application (clean form layout with blank lines/boxes) → Print/Save as PDF.
- **Fillable PDF download** (pdf-lib, AcroForm fields matching enabled sections).
- Equal Housing Opportunity statement + logo glyph (house+equals, drawn SVG/vector) in footer.
- Landlord tips card (off-document): consistent screening criteria, FCRA adverse action,
  link to lease generator tool.
NOT LEGAL ADVICE disclaimer; fair housing reminder (don't ask about protected classes).
