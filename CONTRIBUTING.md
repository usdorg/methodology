# Contributing

Thank you for helping make the method better. We welcome proposals from business owners, customers, researchers and anyone who works with public records.

## Proposals

Open an issue and pick a template:

- **Factor or source.** A new factor, a public record we should use, or a change to how a factor is measured.
- **Error in the method.** Something in the text that is wrong, unclear or out of date.

A proposal needs evidence: a public source, a law or regulation, a study, or data that anyone can check. Changes to weights need a public issue with the reasoning and a test on real data before they are accepted.

To fix a fact about a specific business, use the correction link on its page at usd.org, not this repository.

## Rules for the method

- Every factor has a stable id. If what a factor measures changes, it gets a new id.
- Weights change only with a new version and an entry in [CHANGELOG.md](CHANGELOG.md).
- Thresholds used to detect fake data are not published.

## Pull requests

Small fixes to wording, links and typos are welcome as pull requests. For anything larger, open an issue first.

Pull requests are reviewed and merged by the maintainers listed in [.github/CODEOWNERS](.github/CODEOWNERS).

## Sign-off

We use the [Developer Certificate of Origin](https://developercertificate.org/). Sign each commit to confirm you have the right to submit it under the licenses of this repository:

```
git commit -s -m "Your message"
```

This adds a line like `Signed-off-by: Your Name <you@example.com>`.

## Licenses of contributions

Text you contribute is licensed under [CC BY 4.0](LICENSE). Code you contribute is licensed under [Apache 2.0](LICENSE-CODE).
