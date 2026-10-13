# How a score adds up

A result is built in four steps: a value for each factor, a weighted average of the factors we could check, a confidence level, and a tier.

## 1. A value for each factor

Every factor gets a value from 0 to 1. Counts (years, prices, services, permits) use diminishing returns, so the first years or the first permits count most:

```text
log_cap(x, cap) = min(1, ln(1 + x) / ln(1 + cap))
```

Events in public records (the clean record factor) use one penalty formula, so the same event weighs the same everywhere:

```text
penalty = exp(-sum(severity * exp(-age_years / tau)) / scale)
scale = 50, tau = 3 years, events older than 7 years are not counted
```

Factors that rely on a claim on the website are capped at 0.6. How each factor is counted is described on [Factors and weights](factors.md).

## 2. The result: a weighted average

```text
result = 100 x sum(weight x value) / sum(weight)
```

The sum runs only over factors we could check. When there is nothing to check for a factor that records a positive practice (prices, guarantee, availability), it gets a neutral value: the 40th percentile of companies in the same city and trade, but not more than 0.5. Silence is not punished with a zero and not rewarded either. Factors that need a match to public records (license, clean record, claims match, permits) are not scored without a match: their weight moves to the other factors. A business without a license match gets no page in the directory.

Each factor's share of the result is its contribution, so the contributions add up exactly to the result:

```text
contribution = 100 x weight x value / sum(weight)
```

## 3. Confidence

Confidence says how much of the result rests on strong evidence:

```text
confidence = sum(weight x checked x strength) / sum(weight)
           x (0.7 + 0.3 x min(1, independent source families / 4))
```

Strength is 1.0 for public records and permits, 0.8 for facts on the website such as prices, 0.6 for claims. For the license, clean record and claims match factors it is the quality of the license match: license number on the website and name 1.0, name only 0.8, trade name owner or phone of a license applicant 0.7. Source families are independent kinds of evidence: license records, discipline records, business entity records, permits and the company website.

## 4. Tier

- **Verified** when the business meets the trust conditions: confidence is at least 0.6, the license is active and matched, the clean record value is at least 0.6, website facts agree with records, nothing is flagged, and at least 3 of L1, L3, L4, L12 could be checked.
- **Listed** otherwise: for example when fewer than 5 factors could be checked, nothing was found in public records, confidence is below 0.4, the license is inactive, or one of the trust conditions is not met.
- **Top** only when the data in a city actually separates companies. We test this on the 12 highest results: the middle half must spread at least 8 points, no more than 30% of neighbours may be closer than 1 point, and when we redraw the weights at random 500 times, the places of the top three must stay within 3 positions. A verified business that stays within the top 10 in 80% of redraws becomes Top. Until a city passes the test, there is no Top tier and no rank numbers.

City lists show the tier and are ordered by the result, without rank numbers and without the result as a number.

## Worked example

An example plumbing company in Florida (not a real business). Customer protection is not counted in Florida and customer experience has weight 0 for now, so the weights below add up to 90.

| Factor | What we found | Weight | Value | Contribution |
|---|---|---:|---:|---:|
| L1. State license | active certified plumbing contractor license | 20 | 1.00 | 22.2 |
| L3. Clean record | no events in public records | 12 | 1.00 | 13.3 |
| L4. Years in business | 12 years as a firm, qualifier licensed for 20 years | 12 | 0.82 | 11.0 |
| L5. Trade qualifications | one backflow certificate | 6 | 0.50 | 3.3 |
| L7. Price transparency | 3 published prices, service call fee disclosed | 9 | 0.63 | 6.3 |
| L8. Written guarantee | 12-month workmanship warranty | 5 | 0.45 | 2.5 |
| L9. Availability | 24/7 emergency service and same-day service | 8 | 0.45 | 4.0 |
| L10. Services match | 12 plumbing services listed, city 75th percentile is 20 | 6 | 0.84 | 5.6 |
| L11. Claims match records | website facts agree with records | 6 | 1.00 | 6.7 |
| L12. Permitted work | 8 permits in 12 months (city 75th percentile 20), 17 of 20 completed permits closed with a final inspection | 6 | 0.70 | 4.7 |
| **Result** | | **90** | | **79.7** |

Contributions are rounded to one decimal; the result is computed before rounding.

Every factor in the example was checked, and the evidence comes from five source families, so confidence is 0.88. The company meets the trust conditions, so it is Verified; whether it is shown as Top depends on the city test above.
