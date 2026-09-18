# Security Policy

## Project status

ShomareCart is currently in specification and early development. There is no
supported production release. Security fixes target the latest `main` branch
unless a future release policy states otherwise.

## Reporting a vulnerability

Please do not open a public issue for suspected vulnerabilities.

When the GitHub repository offers private vulnerability reporting, use
**Security → Report a vulnerability**. Otherwise, contact the repository owner
through a private method listed on their GitHub profile and request a secure
reporting channel. Do not send real receiving details, confidential banking
credentials, unrelated personal data, secrets, or exploit data through a public
channel.

A destination card number is routinely shared in Iran to receive a card-to-card
transfer. By itself, it is not an authentication secret and cannot authorize an
outgoing payment. It is nevertheless personal receiving information, so a real
card number or recipient name is unnecessary in a vulnerability report and must
be replaced with fictional data.

Include only the minimum information needed to reproduce the problem:

- affected commit or version;
- affected component;
- impact and realistic attack scenario;
- reproduction steps using fictional data;
- suggested mitigation, if known.

Maintainers should acknowledge a complete report, assess severity, coordinate a fix, and disclose responsibly. Exact response times will be published once the project has an active maintainer rotation.

## Receiving details and confidential credentials

Never submit real receiving details to this repository or its tooling, including
card numbers and recipient names. This is a privacy and data-minimization rule,
not a claim that the card number is a secret credential.

The following are confidential and must never be requested, collected, stored,
displayed, or submitted:

- PINs and first or second/internet banking passwords;
- CVV2 values, expiration dates, and OTPs;
- banking credentials and account balances;
- transaction details or screenshots from a real banking app;
- production encryption keys, management tokens, or private URLs;
- unredacted logs containing personal or financial information.

Use deterministic fictional values from project fixtures. If a real card number
or recipient name is committed accidentally, remove it from public access,
notify the affected person and maintainers privately, and assess privacy or
impersonation risk. If a credential, token, or other secret is exposed, treat it
as compromised and rotate or revoke it at the source. Deleting a Git commit
alone does not make exposed data private or safe.

## Security boundaries

Any implementation must preserve the boundaries in the
[project constitution](./.specify/memory/constitution.md), including encrypted
card-number storage, non-guessable public identifiers, cache-safe deactivation,
strict analytics allow-lists, and the prohibition on collecting bank
credentials. Feature-specific controls must be captured in the active Spec Kit
artifacts.
