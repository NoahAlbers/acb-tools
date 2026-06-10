# Spec — Late Rent Notice Generator

Slug: `late-rent-notice-generator` · Rating seed {value:4.9,count:391}
The highest-intent tool in the suite: a landlord with late rent today. Two document modes, state
cure periods computed into actual calendar deadlines. Builder + live preview layout (use
`tools/rental-application-generator/index.html` as the structural exemplar).

## Builder
1. **Notice type** (segmented):
   - **Friendly reminder** — polite letter, before formal notice ("we noticed rent hasn't arrived…").
   - **Formal Notice to Pay or Quit** — statutory demand referencing state cure period.
2. **State select** → shows state cure-period panel (data below) with "verify current law" note.
3. **Parties & property**: landlord/manager name, tenant name(s), property address (street/city/zip).
4. **The money** — mini ledger with add/remove rows: row = description + amount.
   Presets: "Rent due [Month]" (amount), "Late fee", "Returned payment fee", "Other".
   Optional "payments received" row type (subtracts). Auto **total amount due** shown big.
5. **Dates**: rent was due (date), notice served (date, default today) + **service method**
   chips (hand delivery / posted on door + mailed / certified mail / per lease).
   For pay-or-quit: tool computes and displays the **earliest deadline date** = served date +
   state cure period (count calendar days; when the state uses business/judicial/court days,
   label the computed date "approximately — [state] counts business/court days; verify").
6. **Payment instructions**: how/where to pay (text), contact phone/email.
7. Friendly mode extra: optional personal line (textarea).

## Document output (live preview, print/save-PDF, copy text)
- Friendly: short professional letter, warm tone, total due, how to pay, "if you've already
  sent payment, please disregard."
- Pay-or-quit: formal heading "NOTICE TO PAY RENT OR QUIT", TO/property block, itemized ledger
  table, total, statutory demand paragraph: pay within the state period or surrender possession,
  failure → eviction proceedings may begin; reservation of rights; **Certificate of Service**
  block (method checkboxes, server name/signature/date).
- Footer disclaimers: not legal advice; cure periods change; some cities require additional
  notices; landlord must follow lease grace periods.
- **ACB CTA (custom copy for this tool):** "Notice didn't work? When tenants leave owing rent,
  Advanced Collection Bureau recovers it — no recovery, no fee." (Stronger placement: also show
  an info card in the builder when total due > $0.)

## State cure periods (nonpayment notice to pay or quit) — data to encode
Use exactly these values in a `CURE` object `{AL:{n:'Alabama',d:'7 days'},...}`; `d` is display
text; add `biz:true` where noted (business/court/judicial days). Where there is no statutory
period, say so and recommend a reasonable demand. All entries get the global "verify" hedge.

AL 7 days · AK 7 days · AZ 5 days · AR 3 days (procedures unusual — strongly verify) ·
CA 3 days (biz: excludes weekends & judicial holidays) · CO 10 days · CT 3 days (after the
statutory 9-day grace) · DE 5 days · DC 30 days · FL 3 days (biz: excludes weekends & legal
holidays) · GA Demand for possession — no fixed statutory period (3–5 days customary) ·
HI 5 business days (biz) · ID 3 days · IL 5 days · IN 10 days · IA 3 days · KS 3 days ·
KY 7 days · LA 5 days (unless the lease waives notice) · ME 7 days · MD 10 days · MA 14 days ·
MI 7 days · MN 14 days · MS 3 days · MO No fixed statutory cure period — written demand
recommended · MT 3 business days (biz) · NE 7 days · NV 7 judicial days (biz) · NH 7 days ·
NJ No cure notice generally required for nonpayment before filing (grace rules protect some
tenants — verify) · NM 3 days · NY 14 days · NC 10 days · ND 3 days · OH 3 days · OK 5 days ·
OR 72 hours (may be given after rent is 7 days late; a 144-hour notice may be given after
4 days) · PA 10 days · RI 5 days · SC 5 days · SD 3 days · TN 14 days · TX 3 days (a lease may
set a different period) · UT 3 business days (biz) · VT 14 days · VA 5 days · WA 14 days ·
WV No statutory cure notice — landlord may proceed under WV procedures (verify) · WI 5 days
(month-to-month and most first-year leases, with right to cure) · WY 3 days

Deadline computation: for plain "N days", deadline = served date + N calendar days; for `biz`
entries compute +N skipping weekends and label "approx. — excludes weekends; holidays may
extend"; for the no-statute states, hide the computed deadline and show their note instead.
