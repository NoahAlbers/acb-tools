# Spec — Security Deposit Return Letter Generator

Slug: `security-deposit-return-letter-generator` · Rating seed {value:4.8,count:227}
Deadline-driven, legally required in most states. Builder + live preview (structural exemplar:
`tools/rental-application-generator/index.html`).

## State data
Copy the deposit-return deadlines **verbatim** from the `SD` object in
`tools/lease-agreement-generator/index.html` — fields `n` (name) and `ret` (return deadline) for
all 51 entries, plus the deposit-interest notes embedded in these states' `disc`/`note` entries:
CT, DC, MA, MD, MN, NJ, OH, PA (interest on deposits). Build a compact object
`DEP={AL:{n:'Alabama',ret:'60 days'},...,interest:[...]}`. Same "verify current law" hedging.

## Builder
1. **State** → panel: return deadline, computed **due date** (move-out date + deadline; for
   text like "30 days (10 days if no deductions)" parse the first number for computation and
   show the full text), interest note where applicable.
2. **Outcome** (segmented, drives the whole letter):
   - **Full refund** — no deductions.
   - **Partial refund** — deductions itemized, remainder returned.
   - **No refund** — deductions consume the deposit.
   - **Tenant owes more** — deductions exceed deposit → letter becomes an itemized statement +
     demand for the balance with a pay-by date. Show builder info card: "If the former tenant
     doesn't pay the balance, that's exactly what ACB collects — no recovery, no fee."
3. **Parties & tenancy**: landlord name/address, tenant name(s), rental address, move-in date,
   move-out date, deposit amount held (+ optional pet deposit, + optional interest owed $).
4. **Deductions itemizer** (for outcomes 2–4): rows = category select (Unpaid rent ·
   Cleaning beyond normal use · Repairs beyond normal wear & tear · Unpaid utilities ·
   Missing items/keys · Other) + free-text description ("be specific — e.g. 'replace broken
   bedroom door, $185 invoice'") + amount. Live math panel: deposit − deductions = refund or
   balance owed (color-coded green/red).
5. **Payment/refund details**: refund method + mailing address used (tenant's forwarding
   address; hint about state forwarding-address rules being landlord-favorable when tenant
   never provides one), or pay-by date + payment instructions for balance-owed mode.
6. **Wear-and-tear guard rail** (builder-side education card, not in letter): matted carpet,
   small nail holes, faded paint = normal wear (NOT deductible) vs. stains, holes, broken
   fixtures = damage (deductible). This is the #1 thing that loses deposit disputes.

## Document output
Professional letter: re: line with property address, deposit accounting table (deposit held,
interest if any, itemized deductions with descriptions, total deductions, **refund enclosed /
balance due**), state-deadline sentence ("This statement is provided within the X required by
[State] law"), enclosure line (receipts/invoices recommended), signature block. Print/save-PDF +
copy text. Certificate-of-mailing line optional.
Disclaimers: not legal advice; some states require receipts attached or specific delivery
methods; deadlines/interest rules change.
ACB CTA custom copy: "Deductions bigger than the deposit? ACB recovers what former tenants owe."
