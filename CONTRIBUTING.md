# Contributing to ShomareCart

Thank you for helping make payment-detail sharing simpler and safer. Contributions of product research, translations, accessibility testing, design, documentation, and code are welcome.

## Before you begin

1. Read the [project constitution](./.specify/memory/constitution.md) and the
   active feature's Spec Kit artifacts.
2. Search existing issues before opening a new one.
3. Open an issue before starting a large feature, architecture change, data-model change, or change to privacy/security behavior.
4. Use fictional card numbers and recipient names in issues, commits, fixtures,
   screenshots, logs, and tests. Never include confidential banking credentials
   or real transaction details.

## Ways to contribute

- Clarify product requirements or edge cases.
- Test QR scanning on real device and print combinations using fictional data.
- Improve accessibility, RTL behavior, numeral normalization, or localization readiness.
- Review privacy and security boundaries.
- Improve documentation and examples.
- Specify, plan, and implement an accepted Spec Kit feature.

## Development workflow

1. Fork the repository and create a focused branch from `main`.
2. Make one coherent change per pull request.
3. Add or update tests for behavioral changes.
4. Check responsive behavior, keyboard access, RTL layout, and sensitive-data handling when relevant.
5. Update the active `spec.md`, `plan.md`, `tasks.md`, or checklist when behavior
   or scope changes.
6. Open a pull request using the repository template.

The application stack has not been selected yet. Until implementation begins,
specification changes should keep Markdown portable and links relative.

## Product and safety rules

- Treat a destination card number as normal receiving information in the Iranian
  card-to-card flow, not as an authentication secret or a security breach.
- Display a card number and user-chosen recipient name only with the recipient's
  explicit consent and only where the approved payer flow requires them.
- Do not add payment processing, bank login, PIN, CVV, expiration date, OTP, or balance access.
- Do not claim that ShomareCart verifies identity or card ownership.
- Do not imply that ShomareCart completes or confirms transfers.
- Keep card format rules configurable rather than scattering literal lengths.
- Keep receiving details and confidential credentials out of URLs, metadata,
  analytics, logs, and third-party scripts.
- Public card pages must remain `noindex` and independently usable without analytics.

## Commit and pull-request guidance

Use concise, imperative commit subjects, for example:

```text
Add RTL card-number isolation tests
Clarify public-link privacy disclosure
```

A pull request should explain:

- the user problem it addresses;
- the relevant requirement or acceptance-criterion IDs;
- how it was verified;
- accessibility and RTL impact;
- privacy and security impact;
- any remaining assumptions or follow-up work.

## Reviews

Maintainers may request changes when a proposal conflicts with the constitution
or active feature specification, expands financial scope, weakens privacy or
accessibility, or lacks appropriate verification. Discussion should stay focused
on the work, be respectful, and follow the [Code of Conduct](./CODE_OF_CONDUCT.md).

## Reporting vulnerabilities

Do not open a public issue for a vulnerability. Follow [SECURITY.md](./SECURITY.md).
