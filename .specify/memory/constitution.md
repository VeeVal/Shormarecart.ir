# ShomareCart Constitution

## Core Principles

### I. Payment-Information Utility, Never a Bank

ShomareCart MUST remain an information-sharing utility. It MUST NOT hold, move,
initiate, authorize, or confirm money transfers. It MUST NOT request or collect a
bank password, PIN, CVV, expiration date, one-time password, account balance, or
national identity number for the core flow. Every payer MUST complete the
transfer in their own banking application, and every interface MUST use language
that accurately describes ShomareCart's limited role.

Identity or card ownership MUST NOT be presented as verified without a real,
documented verification process. This boundary protects users from misplaced
trust and keeps product scope, legal exposure, and security risk explicit.

### II. Privacy and Security by Design

In Iran, sharing a destination card number is a common and necessary part of
card-to-card transfers. A card number alone is not an authentication secret and
does not authorize an outgoing payment. Sharing it for the purpose of receiving
money MUST NOT be described as a security breach or treated as equivalent to
sharing a PIN, password, CVV2, expiration date, or one-time password. After
explicit user consent, ShomareCart MAY display the card number and user-chosen
recipient name as the public receiving details that the payer needs.

This intended sharing does not make public receiving details unrestricted data.
The system MUST collect, store, expose, and retain only the minimum data required
for the approved user flow. Card numbers MUST be encrypted at rest. Names, card
numbers, public identifiers, management tokens, and clipboard values MUST NOT
enter URLs, page metadata, logs, analytics, traces, error reports, screenshots,
or third-party scripts. Public identifiers MUST be non-sequential and
non-guessable; public card pages MUST be excluded from indexing and MUST support
prompt deactivation without stale-cache disclosure.

PINs, first or second/internet passwords, CVV2 values, expiration dates, OTPs,
banking credentials, and account balances are confidential. ShomareCart MUST
NEVER request, store, display, or transmit them.

All development, tests, examples, issues, and documentation MUST use fictional
payment data. Security-sensitive changes MUST include threat analysis and tests
for enumeration, injection, cache invalidation, token leakage, bidirectional-text
handling, and telemetry exposure as applicable. Local legal and privacy review is
a release gate, not a substitute for these engineering requirements.

### III. Scan, Confirm, Copy

The payer's core journey MUST remain: scan the controlled HTTPS QR URL, confirm
the displayed recipient name, and copy the normalized card number. The recipient
name MUST appear before the card number, and the interface MUST tell the payer to
confirm the bank-provided name before transferring. The copied value MUST contain
only normalized ASCII digits, without spaces, labels, separators, or direction
marks, and a manual-copy fallback MUST exist when clipboard access fails.

QR assets MUST prioritize reliable scanning over decoration: dark modules on
white, a sufficient quiet zone, no animated code, and verification on
representative phones, screens, lighting conditions, and grayscale prints.
ShomareCart MUST never display a payment-success state because it cannot observe
or confirm the bank transfer.

### IV. Accessibility, RTL, and Localization First

Every production user flow MUST target WCAG 2.2 AA and remain operable by
keyboard, screen reader, touch, and at 200% zoom. Controls MUST retain visible
focus, programmatic labels, specific errors, accessible status announcements,
and touch targets of at least 44 by 44 pixels. Nonessential motion MUST respect
reduced-motion preferences.

Right-to-left and left-to-right layouts MUST be designed and tested together.
Card-number strings MUST render in an isolated left-to-right container so digit
groups cannot reverse. Supported local numeral sets MUST normalize to the same
stored ASCII digits. User-facing strings MUST live in localization resources,
and the experience MUST remain usable from 320-pixel viewports upward without
horizontal scrolling or obscured actions.

### V. Spec-Driven, Testable, Minimal Delivery

Implementation MUST follow the approved Spec Kit artifacts for the active
feature. The feature's `spec.md` defines user needs, scope, requirements, and
acceptance scenarios; `plan.md` defines architecture, design decisions, data
contracts, and implementation constraints; `tasks.md` defines the ordered work;
and feature checklists define release evidence. The constitution is the only
project-wide product and engineering authority outside feature specifications.
A change that alters product behavior MUST update the affected Spec Kit
artifacts in the same pull request.

Features MUST be delivered in the smallest milestone that solves an approved
user problem. Card format, validation, grouping, fixtures, and messages MUST read
from one versioned configuration rather than scattered literals. Behavioral
changes MUST include tests proportional to risk. Contributors and agents MUST
use Codebase Memory for discovery and impact analysis, check index coverage, and
read the exact files they change. Complexity or scope beyond the MVP MUST be
justified in the feature specification and accepted before implementation.

## Product, Data, and Technical Constraints

- The MVP MUST be a responsive web product; native apps, bank integrations,
  payment processing, balances, transaction history, multi-card teams, and
  dynamic invoices remain out of scope until separately specified.
- Payers MUST NOT need an account. Recipient ownership MUST use either an
  approved authentication flow or a separate high-entropy management token.
- Card digit length and grouping MUST come from a versioned configuration. The
  brief's provisional 12-digit value MUST NOT become a production rule until the
  launch market and provider format are confirmed.
- Public QR payloads MUST contain only a canonical HTTPS URL on a controlled
  domain. Card details MUST NOT appear in URLs, sitemaps, search results, or
  social-preview metadata.
- Server-side validation MUST be authoritative. HTTPS, secure response headers,
  CSRF controls where applicable, abuse-conscious rate limiting, encrypted
  backups, secret scanning, and dependency scanning are release requirements.
- Public card rendering and copying MUST work without analytics, advertising,
  session replay, heatmaps, chat widgets, or other third-party scripts.
- Mobile Largest Contentful Paint MUST be at most 2.5 seconds at the production
  75th percentile. The copy action MUST remain stable and usable during load.
- Analytics MUST use an explicit property allow-list and MUST reject sensitive
  or free-form values. Analytics failure or disablement MUST NOT break core use.

## Development Workflow and Quality Gates

1. A feature MUST begin with `$speckit-specify` and an approved `spec.md`.
   Material ambiguity MUST be resolved with `$speckit-clarify` before planning.
2. `$speckit-plan` MUST produce an implementation plan that identifies
   requirement IDs, user-visible states, data boundaries, accessibility and RTL
   impact, test strategy, and rollback or deactivation behavior where relevant.
3. `$speckit-tasks` MUST produce dependency-ordered, independently verifiable
   work before implementation begins. Required release checks MUST be captured
   with `$speckit-checklist`.
4. Implementation MUST preserve unrelated user work, use fictional centralized
   fixtures, and keep user-facing copy localizable. The Codebase Memory index
   MUST be refreshed after substantial structural changes.
5. Review MUST verify the happy path and failure states, including invalid input,
   offline or network failure, clipboard denial, unavailable public cards,
   deactivation, slow loading, and directionality.
6. Release evidence MUST include automated checks, manual keyboard review,
   accessibility results, responsive LTR and RTL screenshots, QR device and
   print tests, sensitive-data boundary checks, and production format approval.
7. A pull request MUST state the requirements covered, verification performed,
   privacy and security impact, and remaining assumptions. It MUST follow
   `CONTRIBUTING.md`, `SECURITY.md`, and the pull-request template.

## Governance

This constitution defines the project's non-negotiable product and engineering
rules. It supersedes conflicting contributor habits, implementation shortcuts,
and workflow documents. The PRD and technical documents may add detail but MUST
NOT weaken this constitution.

An amendment MUST be proposed in a pull request that explains the reason,
affected principles and documents, migration impact, and version change. Review
MUST explicitly assess user safety, privacy, accessibility, RTL behavior, product
scope, and contributor impact. Approval by the active maintainers is required
before merge.

Constitution versions follow semantic versioning:

- MAJOR for removal or backward-incompatible redefinition of a principle or
  governance obligation.
- MINOR for a new principle, new governance section, or materially expanded
  mandatory guidance.
- PATCH for clarifications and non-semantic wording corrections.

Every specification, implementation plan, task list, and pull request MUST be
checked for constitutional compliance. Any temporary exception MUST be explicit,
time-bounded, linked to a tracking issue, and include a safe removal plan. A
release MUST NOT proceed while a non-negotiable principle is knowingly violated.

**Version**: 1.1.0 | **Ratified**: 2026-09-18 | **Last Amended**: 2026-09-18
