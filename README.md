# ShomareCart

ShomareCart is an open-source, mobile-first card-number QR platform for people who would otherwise need to read payment details aloud. A payer scans a reusable QR, confirms the recipient name, copies the card number, and completes the transfer in their own banking app.

> [!IMPORTANT]
> ShomareCart is in the specification phase. It does not yet process payments,
> verify card ownership, or provide a production service.

## Why this exists

Taxi drivers, shopkeepers, street performers, and individuals often repeat long card numbers—sometimes several times to the same person. That is slow, disruptive, and easy to get wrong. ShomareCart aims to replace that conversation with three clear steps: **scan, confirm, copy**.

## Product principles

- ShomareCart shares payment details; it never handles money.
- Payers complete transfers in their existing banking app.
- The recipient name is prominent so payers can confirm it before transferring.
- Public pages collect and expose the minimum necessary data.
- Right-to-left languages, local numerals, accessibility, and low-end devices are first-class requirements.
- Card-number length and grouping are centrally configurable and must be confirmed for the launch market.

## Card numbers and confidential credentials

In Iran, giving someone a destination card number to receive a card-to-card
transfer is common. A card number alone is not an authentication secret and does
not authorize an outgoing payment. ShomareCart is designed to share that number
and a user-chosen recipient name with the payer after the recipient consents.

PINs, first or second/internet banking passwords, CVV2 values, expiration dates,
OTPs, account balances, and banking credentials are confidential. ShomareCart
will never ask for, store, or display them. Public receiving details are still
personal information: they must not leak into URLs, search results, analytics,
logs, or unrelated public discussions.

## Specification workflow

The [project constitution](./.specify/memory/constitution.md) defines the
non-negotiable product and engineering principles. Features are developed with
Spec Kit: `spec.md` defines requirements, `plan.md` records design and technical
decisions, `tasks.md` orders implementation work, and feature checklists capture
release evidence.

## Project status

- [x] Project constitution and product boundaries
- [x] Spec Kit development workflow
- [ ] Clickable prototype
- [ ] Application implementation
- [ ] Usability and QR device testing
- [ ] Local legal and privacy review
- [ ] Production release

## Contributing

Contributions are welcome. Start with [CONTRIBUTING.md](./CONTRIBUTING.md), follow
the [Code of Conduct](./CODE_OF_CONDUCT.md), and use fictional receiving details
in issues, examples, screenshots, tests, and logs. This repository rule protects
privacy and does not mean a destination card number is an authentication secret.

For major product or architecture changes, open an issue before implementation
so the proposal can be discussed against the active feature specification and
the constitution.

## Security

Do not report vulnerabilities, confidential credentials, or anyone's real
receiving details in a public issue. Follow [SECURITY.md](./SECURITY.md) for safe
reporting and data-handling expectations.

## AI-assisted development

The repository includes Spec Kit workflows and a persistent Codebase Memory
rule. Agents should use the code graph for discovery and impact analysis, then
inspect the exact source before making changes. See
[`.cursor/rules/codebase-memory.mdc`](./.cursor/rules/codebase-memory.mdc).

## License

Licensed under the [MIT License](./LICENSE).
