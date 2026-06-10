# Webflow page kit — Free Tools hub (`/resources`)

A landing page that links every tool. This concentrates internal links (good for SEO) and gives
the nav menu a single "Free Tools" destination.

## Page settings

- **Title tag:** Free Tools for Landlords & Property Managers | Advanced Collection Bureau
- **Meta description:** Free calculators and document generators for landlords: lease agreement builder, rental application, ROI, cap rate, NOI, mortgage, turnover cost, and the 70% rule. No signup.

## Suggested nav placement

Add a **"Free Tools"** dropdown to the main Webflow navigation listing all tools (or linking to
this hub page). Tools earn links and rank; the dropdown routes that traffic toward the
collections funnel.

## Page structure

1. **H1:** Free Tools for Landlords & Property Managers
2. Intro:
   > Everything here is 100% free — no accounts, no email walls, no paywalled downloads. Built by Advanced Collection Bureau, the rental-debt recovery specialists, for the landlords and property managers we serve.
3. **Card grid** (link cards, one per tool — title + one-liner):

| Tool | URL | One-liner |
|---|---|---|
| Lease Agreement Generator | /resources/lease-agreement-generator | Build a state-specific lease in 5 minutes, or download a fillable PDF. All 50 states + D.C. |
| Rental Application Generator | /resources/rental-application-generator | A customizable, fair-housing-safe application with fillable PDF download. |
| Late Rent Notice Generator | /resources/late-rent-notice-generator | Friendly reminder or formal pay-or-quit notice — state cure periods and deadlines computed. |
| Security Deposit Return Letter | /resources/security-deposit-return-letter-generator | Itemized disposition letter with your state's deadline, incl. the balance-owed path. |
| Rent Increase Notice Generator | /resources/rent-increase-notice-generator | Notice periods validated, rent-control caps flagged, effective date computed. |
| Rental Property ROI Calculator | /resources/rental-property-roi-calculator | Cash flow, cash-on-cash, cap rate, IRR, and year-by-year projections. |
| Mortgage Calculator | /resources/mortgage-calculator | Full PITI with PMI auto-drop, extra payments, and amortization. |
| Cap Rate Calculator | /resources/cap-rate-calculator | Solve cap rate, max price, or required NOI — instantly. |
| NOI Calculator | /resources/net-operating-income-calculator | Itemized income & expenses with benchmark checks. |
| Turnover Cost Estimator | /resources/turnover-cost-estimator | What a turnover really costs vs. keeping your tenant. |
| 70% Rule Calculator | /resources/70-percent-rule-calculator | Max allowable offer for fix & flip deals. |
| Move-In/Move-Out Checklist | /resources/move-in-move-out-checklist-creator | Room-by-room inspection with photos and a signed-ready PDF. |
| Prorated Rent Calculator | /resources/prorated-rent-calculator | Exact partial-month rent for any move-in date and billing day. |
| Rent Increase Calculator | /resources/rent-increase-calculator | Project rent growth over 1–50 years with CSV export. |
| Security Deposit Interest Calculator | /resources/security-deposit-interest-calculator | Daily-compounded interest plus state deposit rules. |
| + any remaining legacy tools | | Rental yield, eviction notice — can be ported the same way |

4. CTA band at the bottom (same copy as the tools' CTA band):
   > **Tenant left owing money?** Advanced Collection Bureau has recovered over $85 million in unpaid rent, fees, and damages. No recovery, no fee. [Get Started](https://www.advancedcb.com/) · (321) 633-4999

## JSON-LD for the hub page

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "CollectionPage",
  "name": "Free Tools for Landlords & Property Managers",
  "url": "https://www.advancedcb.com/resources",
  "publisher": {"@type": "Organization", "name": "Advanced Collection Bureau", "url": "https://www.advancedcb.com"},
  "hasPart": [
    {"@type": "WebApplication", "name": "Lease Agreement Generator", "url": "https://www.advancedcb.com/resources/lease-agreement-generator"},
    {"@type": "WebApplication", "name": "Rental Application Generator", "url": "https://www.advancedcb.com/resources/rental-application-generator"},
    {"@type": "WebApplication", "name": "Late Rent Notice Generator", "url": "https://www.advancedcb.com/resources/late-rent-notice-generator"},
    {"@type": "WebApplication", "name": "Security Deposit Return Letter Generator", "url": "https://www.advancedcb.com/resources/security-deposit-return-letter-generator"},
    {"@type": "WebApplication", "name": "Rent Increase Notice Generator", "url": "https://www.advancedcb.com/resources/rent-increase-notice-generator"},
    {"@type": "WebApplication", "name": "Rental Property ROI Calculator", "url": "https://www.advancedcb.com/resources/rental-property-roi-calculator"},
    {"@type": "WebApplication", "name": "Mortgage Calculator", "url": "https://www.advancedcb.com/resources/mortgage-calculator"},
    {"@type": "WebApplication", "name": "Cap Rate Calculator", "url": "https://www.advancedcb.com/resources/cap-rate-calculator"},
    {"@type": "WebApplication", "name": "Net Operating Income Calculator", "url": "https://www.advancedcb.com/resources/net-operating-income-calculator"},
    {"@type": "WebApplication", "name": "Turnover Cost Estimator", "url": "https://www.advancedcb.com/resources/turnover-cost-estimator"},
    {"@type": "WebApplication", "name": "70% Rule Calculator", "url": "https://www.advancedcb.com/resources/70-percent-rule-calculator"}
  ]
}
</script>
```
