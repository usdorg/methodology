# Factors and weights

We assess a business on 12 factors. Each factor has a stable id (L1 to L12); if what a factor measures changes, it gets a new id, so old results stay comparable. This is version 3.0 of 2026-10-12.

## Weights

Weights add up to 100 within each group of trades. A factor with weight 0 is not active yet.

| Factor | Trades | In-home services | Technical services | Exterior services |
|---|---:|---:|---:|---:|
| [L1. State license](#l1-state-license) | 20 | 10 | 8 | 8 |
| [L2. Customer protection (insurance, bond, workers' comp)](#l2-customer-protection-insurance-bond-workers-comp) | 10 | 18 | 10 | 18 |
| [L3. Clean record](#l3-clean-record) | 12 | 10 | 12 | 12 |
| [L4. Years in business](#l4-years-in-business) | 12 | 14 | 13 | 15 |
| [L5. Trade qualifications](#l5-trade-qualifications) | 6 | 4 | 18 | 5 |
| [L6. Customer experience (our own survey)](#l6-customer-experience-our-own-survey) | 0 | 0 | 0 | 0 |
| [L7. Price transparency](#l7-price-transparency) | 9 | 14 | 12 | 12 |
| [L8. Written guarantee](#l8-written-guarantee) | 5 | 9 | 7 | 8 |
| [L9. Availability](#l9-availability) | 8 | 9 | 8 | 8 |
| [L10. Services match](#l10-services-match) | 6 | 6 | 6 | 8 |
| [L11. Claims match records](#l11-claims-match-records) | 6 | 6 | 6 | 6 |
| [L12. Permitted work](#l12-permitted-work) | 6 | 0 | 0 | 0 |

Trades in each group: Trades: plumbing, drain cleaning, water heaters, HVAC; In-home services: house cleaning, maid service, move-out cleaning; Technical services: carpet and upholstery cleaning, air duct and dryer vent cleaning, tile and grout, chimney; Exterior services: pressure washing, gutter cleaning, window cleaning, roofing, solar.

## How strong a fact is

The same fact can come from different places. We count it by the strength of its evidence:

| Evidence | Example | Strength |
|---|---|---:|
| Public record | License found in the state register | 1 |
| Document on the website | Certificate of insurance published as a file | 0.8 |
| Specific claim on the website | Insured for $1,000,000 with a named insurer | 0.6 |
| Vague claim on the website | Fully insured | 0.35 |
| Nothing found | Not scored: the factor's weight moves to the others | not scored |

A claim on a website alone never counts as much as a record. For factors that rely on claims, the credit a claim can get is capped.

## L1. State license

Weight for trades: **20**.

- **What we measure.** Whether the business holds an active state license for the trade, and which class.
- **Source.** Florida Department of Business and Professional Regulation (DBPR), Construction Industry Licensing Board licensee file.
- **Why it matters.** A license means the contractor met state requirements and can be held to account by the licensing board.
- **How we count it.** An active license counts 1, an inactive one 0. The class is multiplied in: a certified plumbing contractor license (CFC, valid in the whole state) counts 1.0, a registered license (RF, valid only where the local exam was passed) counts 0.7. If we cannot match the business to any license, the factor is not scored and the business gets no page in the directory.
- **How to improve.** Show your full state license number on the website so it can be matched to the state record.

How sure we are that a license belongs to this business (license number on the website and name, name only, trade name owner, or phone of a license applicant) affects our confidence, not the business's result. A weak match on our side is not the company's fault.

## L2. Customer protection (insurance, bond, workers' comp)

Weight for trades: **10**.

- **What we measure.** General liability insurance, bond, workers' compensation and background checks of staff.
- **Source.** The company website. Florida has no public register of contractor insurance, so in Florida this is shown as claimed and does not count toward the result.
- **Why it matters.** If something goes wrong in your home, insurance and a bond decide who pays.
- **How we count it.** Weighted sum of four parts: insurance 45%, bond 20%, workers' compensation 20%, background checks 15%. Each part counts by the strength of its evidence: vague claim 0.35, specific claim 0.6, document on the website 0.8, public record 1.0.
- **How to improve.** Publish your insurer, policy limits and a current certificate of insurance; list your bond and workers' comp.

## L3. Clean record

Weight for trades: **12**.

- **What we measure.** Events in public records: board citations and final orders, suspended or revoked licenses, unlicensed activity, payouts from the recovery fund, workers' comp stop-work orders, administrative dissolution and late annual reports.
- **Source.** Construction Industry Licensing Board discipline records and Florida Homeowners' Construction Recovery Fund claims; Florida Division of Workers' Compensation stop-work orders; Florida Division of Corporations (Sunbiz).
- **Why it matters.** Past problems with the board or the state are the clearest public warning a customer can get.
- **How we count it.** A record with no events counts 1. Each event has a severity from 0 to 100 (listed below) and fades with age: its weight halves roughly every two years, and events older than 7 years are not counted. The factor equals exp(-sum of faded severities / 50), so one fresh final order (severity 40) gives 0.45 and the same order three years later gives 0.75. If we cannot match the business to records, the factor is not scored.
- **How to improve.** Resolve open complaints with the licensing board; keep annual reports and insurance current.

| Event | Severity |
|---|---:|
| Licensing board citation | 12 |
| Licensing board final order | 40 |
| License suspended or revoked | 70 |
| Unlicensed activity | 60 |
| Payout from the Homeowners' Construction Recovery Fund | 50 |
| Workers' comp stop-work order or lapse in coverage | 15 |
| Administrative dissolution of the business entity | 15 |
| Late annual report | 5 |

## L4. Years in business

Weight for trades: **12**.

- **What we measure.** How long the business has operated, and how long its qualifying license holder has been licensed.
- **Source.** First license date in DBPR records, filing date in Sunbiz when the address matches, and first appearance of the website in the Internet Archive.
- **Why it matters.** A firm that has worked for years has a history that can be checked.
- **How we count it.** Firm years are the median of the dates we can confirm. Years count with diminishing returns, log_cap(years, 25): 5 years give 0.55, 10 years 0.74, 25 years or more 1. The qualifier's own years can only add: the factor is the larger of the firm's value and 75% firm plus 25% qualifier, so a new firm run by an experienced contractor is not treated as a beginner.
- **How to improve.** Keep the business entity and license in good standing; years are counted from state records, not from the website.

## L5. Trade qualifications

Weight for trades: **6**.

- **What we measure.** Certifications relevant to the trade, such as backflow and cross-connection certificates or manufacturer certifications for water heaters.
- **Source.** The company website, checked in the issuer's public locator where one exists.
- **Why it matters.** Some jobs need training beyond the base license.
- **How we count it.** Each accepted personal certification counts 1, trade associations and manufacturer programs 0.25 each; the total counts with diminishing returns, log_cap(total, 3): one certification gives 0.5, three or more give 1. A certification we only see claimed on the website is capped at 0.6.
- **How to improve.** List certifications with the issuing body and number so they can be checked in the issuer's locator.

Accepted certifications: plumbing: ASSE 6010, ASSE 5110, Green Plumbers USA; hvac: NATE, EPA 608 (claimed only); water heater: Navien, Rinnai, Bradford White.

## L6. Customer experience (our own survey)

Weight for trades: **0**.

- **What we measure.** Whether customers would hire the company again, from our own survey of verified customers.
- **Source.** Our own survey. Not active yet; until then this factor has no weight.
- **Why it matters.** Records show whether a company is legitimate. Only customers can say whether the work was good.
- **How we count it.** The lower bound of the 90% Wilson interval for the share of customers who would hire the company again, so a few answers cannot outweigh many. With fewer than 10 answers the factor is not scored.

We do not copy ratings or reviews from other platforms.

## L7. Price transparency

Weight for trades: **9**.

- **What we measure.** Prices published for common jobs, flat or upfront pricing, and whether the service call fee is disclosed.
- **Source.** The company website.
- **Why it matters.** Published prices let you compare before you call and reduce surprises on the invoice.
- **How we count it.** Weighted sum: number of published prices 50% (a price per job or per hour counts 1, a "starting at" price 0.5, with diminishing returns up to 5), upfront or flat pricing 20%, disclosed service call fee 15%, price compared with the city median 15% (not active until services are normalized across companies; its weight moves to the other parts).
- **How to improve.** Publish prices for your common jobs (not only "from $X" or coupons) and your service call fee.

## L8. Written guarantee

Weight for trades: **5**.

- **What we measure.** A workmanship warranty with a stated length and coverage, and a satisfaction guarantee that says how it works.
- **Source.** The company website.
- **Why it matters.** A written guarantee tells you what happens if the repair fails.
- **How we count it.** Warranty 60%: 0.95 x log_cap(months, 24), so 12 months give 0.76 and 24 months or more give 0.95; a lifetime warranty with stated conditions gives 1; a warranty on parts only counts half. Satisfaction guarantee 40%, counted only when it says how it works (redo, refund). Because this is a claim on the website, the factor is capped at 0.6.
- **How to improve.** State your workmanship warranty in months, what it covers and how to claim it.

## L9. Availability

Weight for trades: **8**.

- **What we measure.** Emergency service hours, same-day and weekend service, online booking.
- **Source.** The company website. Later, a measured response to a test call.
- **Why it matters.** For a burst pipe, who answers at night matters more than anything else.
- **How we count it.** Weighted sum: 24/7 emergency service 20% (rarer in the trade, so it counts more: with it 0.84, without it 0.34 for plumbers), same-day service 15%, weekend service 15%, online booking 20%, measured response to a test call 30% (not active yet). Claims are capped at 0.6.
- **How to improve.** Say exactly when you answer emergency calls and offer online booking.

## L10. Services match

Weight for trades: **6**.

- **What we measure.** Which services in the trade the company lists, and whether the trade is its main line of work.
- **Source.** The company website.
- **Why it matters.** A company that does your kind of job every day is more likely to do it well.
- **How we count it.** The number of listed services in the trade family counts with diminishing returns up to the 75th percentile of companies in the same city and trade. It is multiplied by 1.0 when the trade is the company's main line of work and 0.7 otherwise.
- **How to improve.** List each service you offer on its own page or line.

## L11. Claims match records

Weight for trades: **6**.

- **What we measure.** Whether the founding year, license number and address on the website agree with state records.
- **Source.** The company website compared with DBPR and Sunbiz records.
- **Why it matters.** A website that states facts the records do not support is a reason to check more carefully.
- **How we count it.** Works like the clean record factor: no mismatch counts 1, and each unexplained mismatch lowers the value, for example a founding year on the website well before any record of the business. A license number on the website that is inactive or belongs to another business is flagged and keeps the listing from being Verified. The exact severities stay private, as for other checks of fake data.
- **How to improve.** Make sure the founding year, license number and address on your website match state records.

## L12. Permitted work

Weight for trades: **6**.

- **What we measure.** Building permits pulled by the company in the last 12 months, and the share closed with a final inspection.
- **Source.** City and county permit portals (in the Tampa Bay area: City of Tampa, Hillsborough, Pinellas and Pasco counties).
- **Why it matters.** Permits closed with a final inspection show work that an inspector signed off on.
- **How we count it.** Weighted sum: permit volume 50%, with diminishing returns up to the 75th percentile of companies in the same city and trade (so size alone cannot win), and the share of completed permits closed with a final inspection 50%, as the lower bound of the 90% Wilson interval. A final inspection counts when the inspection record shows it approved or passed. An expired permit counts as not closed; a completed permit with no inspection on record is left out of the share. With fewer than 10 completed permits the share is not scored and its weight moves to volume. Without a match to permit records the factor is not scored.
- **How to improve.** Pull permits for permitted work and close them with a final inspection.

## Detection of fake data

Separately from the 12 factors, we look for signs that data is not genuine, such as lead generation fronts posing as local companies or addresses that are mailbox services. No single sign proves anything; we act only when several agree. We describe these checks by principle only. The exact thresholds stay private so they cannot be gamed.

The machine-readable version of this page, with every formula and worked examples, is in our public [methodology repository](https://github.com/usdorg/methodology).
