# Changelog

Every change to the method is recorded here with the reason. Changing what a factor measures gives it a new id.

## 3.0 (2026-10-13)

- Weights, formulas and the machine-readable factor file ([levers.yaml](levers.yaml)) are published, as promised in 0.1. How a result adds up: [docs/calculation.md](docs/calculation.md).
- Principles describe what listings show today: every section names its source and dates, how a score adds up is public on the methodology pages, a business without a license match gets no page and factors without evidence are not scored.
- First version published with weights and formulas. Earlier versions 1 and 2 (September 2026) were used only to test the method on pilot data and were never shown on the site.
- One shape for every count (log_cap, diminishing returns) and one formula for every penalty, so the same event weighs the same in every factor.
- Factors that need a match to public records (license, clean record, claims match) are not scored when there is no match, instead of getting an assumed value.
- How sure we are about the license match moves from the license factor into confidence: a weak match on our side no longer lowers the business's result.
- License class counts: a statewide certified license 1.0, a locally registered license 0.7.
- Claims seen only on the website (qualifications, guarantee, availability) are capped at 0.6.
- Permit volume is capped at the 75th percentile of the city, so size alone cannot win.
- In Florida, customer protection (insurance, bond, workers' comp) is shown as claimed and does not count, because the state has no public insurance register.
- A Top tier and rank numbers appear only when the data in a city actually separates companies (discrimination test).
- Tiers are Verified and Listed. Verified means the business meets the trust conditions (confidence, an active matched license, a clean record, website facts that agree with records, enough registry factors checked); every other business is Listed. Top appears only in a city that passes the discrimination test.
- The result is not shown as a number in city lists: lists show the tier and are ordered by the result.
- Permitted work: whether a completed permit was closed with a final inspection is now read from the inspection records of each permit, as this method describes, instead of being inferred from the permit status. An expired permit counts as not closed; a completed permit with no inspection on record is left out of the share.

## 0.1 (2026-10-12)

- First public release: principles and the 12 factors (L1 to L12) with sources, reasons and how to improve.
- Weights, formulas and the machine-readable factor file are not included yet. They come with version 3.0, before any score is shown on usd.org.
