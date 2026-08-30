# Profitable AI List Design

## Purpose

Build an English-language Awesome List that helps founders, builders, and researchers discover AI products with verifiable commercial traction. The list covers AI directories, SaaS, companions, games, focused tools, image and video products, model gateways, developer tools, and voice or audio products.

The project must be useful as an independent reference. It must not reserve privileged placement for the maintainer's products or describe unverified products as profitable.

## Inclusion Standard

Every listed product must have all of the following:

- A working canonical product URL.
- A concise, neutral description of what the product does.
- A public commercial signal from one of these evidence classes:
  - **Revenue**: disclosed revenue, ARR, MRR, GMV, or profitable status.
  - **Customers**: disclosed paying-customer or paid-subscriber count.
  - **Funding**: a disclosed institutional funding round or acquisition.
  - **Paid product**: a public paid plan when stronger evidence is not available.
- A direct source URL supporting the commercial signal.

Revenue, customers, funding, and paid availability are separate claims. Funding and pricing must never be described as revenue or profitability. Evidence should be official or founder-authored when possible; reputable reporting is acceptable when the primary source is unavailable. Unsourced estimates, scraped revenue databases, affiliate roundups, and copied marketing claims are excluded.

## Information Architecture

The root `README.md` is the primary artifact and follows Awesome List conventions:

1. Title, Awesome badge, and succinct theme description.
2. A short scope note explaining that commercial validation is broader than net profitability.
3. A `Contents` section with a single flat list of category links.
4. A signal legend.
5. Curated categories containing consistently formatted bullet entries.
6. A short methodology section that explains evidence freshness and corrections.
7. A contribution section outside the table of contents.

Each entry uses this shape:

```markdown
- [Product](https://product.example) - Objective description. **Revenue:** Verifiable claim ([source, year](https://evidence.example)).
```

The initial release targets roughly 40 to 60 strong entries. Quality and evidence clarity take priority over category symmetry or list length. Formind and Veline AI are deliberately not included in the initial seed because the maintainer intends to submit them later under the same evidence rules.

## Repository Files

- `README.md`: Curated list, scope, evidence legend, and methodology.
- `CONTRIBUTING.md`: Eligibility rules, source hierarchy, entry format, disclosure requirement, and review checklist.
- `CODE_OF_CONDUCT.md`: Contributor behavior expectations.
- `LICENSE`: CC0 1.0, matching the Awesome List recommendation for curated data.
- `.github/ISSUE_TEMPLATE/add-product.yml`: Structured nomination form.
- `.github/ISSUE_TEMPLATE/report-problem.yml`: Correction and broken-link form.
- `.github/ISSUE_TEMPLATE/config.yml`: Issue-template configuration.
- `.github/pull_request_template.md`: Submission checklist.
- `.github/workflows/awesome-lint.yml`: Markdown convention checks.
- `.github/workflows/links.yml`: Scheduled and pull-request link checks.

## Maintenance and Trust

Contributors must disclose whether they are a founder, employee, investor, affiliate, or agency representative for a submitted product. Self-submission is allowed but does not relax the evidence standard. Product ordering is alphabetical within a category, preventing paid-looking placement.

Sources include a year wherever the publication date is visible. Maintainers may remove entries whose product or evidence link disappears, whose claim is materially corrected, or whose business is no longer AI-centered. Corrections use a dedicated issue form.

## Validation

Before delivery:

- Run `npx awesome-lint` against the repository and resolve actionable failures.
- Check all Markdown links with Lychee, allowing documented exceptions only for sites that block automated clients.
- Run local structural checks for duplicate product URLs, missing evidence labels, missing source links, and malformed entry punctuation.
- Review the final diff to confirm that Formind and Veline AI were not seeded and that no signal class is overstated.

