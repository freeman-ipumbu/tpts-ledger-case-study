# TPTS Nexus

**A unified financial operations platform for payment orchestration, lending,
collections, treasury, reconciliation and risk.**

**Namibian-born · Africa-ready.**

TPTS Nexus turns fragmented payment and credit operations into one controlled,
auditable operating system. It combines a payment orchestration layer with loan
origination and servicing, verified settlement evidence, maker-checker treasury
controls, reconciliation, smart references, risk oversight and secure
administration.

[Open the protected demonstration](https://tpts-ledger.pages.dev)

> The hosted workspace is access-controlled and uses explicitly synthetic
> demonstration data. This public repository is a case study only; application
> source, credentials, customer information and operational data are private.

## What it solves

- Wrong or missing payment references that strand money in suspense.
- Disconnected bank, payment-provider, billing and lending workflows.
- Manual loan decisions, mandates, collections and disbursement tracking.
- Treasury actions without reliable segregation of duties or execution proof.
- Provider catalogues that look connected before credentials and adapters exist.
- Audit trails spread across spreadsheets, email and separate systems.

## Built for African operating reality

Nexus begins with Namibia's NAD operations and the controls TPTS needs today,
while keeping entities, currencies, providers and product rules bounded so the
platform can expand market by market. The ambition is continental; the trust
model stays local, explicit and evidence-led.

## Product surfaces

| Workspace | Capabilities |
| --- | --- |
| Nexus cockpit | Portfolio, collections, liquidity, arrears and control priorities |
| Origination | Customers, masked KYC, products, applications and human decisions |
| Servicing | Loan accounts, exact schedules, mandates and controlled collections |
| Treasury | Maker-checker disbursement queue and one-use bank evidence |
| ClearLedger | Statement import, matching, exceptions, allocations and posting |
| Integrations | TPTS OneGate, bounded bank import, Gemini advisory and connector catalogue |
| Administration | Invitations, roles, permissions, connector lifecycle and audit controls |

## Control philosophy

Nexus never equates a browser return, catalogue entry or saved configuration
with money movement. A financial state changes only from authenticated provider
data or exact imported bank evidence. Every privileged mutation is role-gated,
idempotent and audit-recorded. Manual financial decisions enforce maker-checker
separation.

See [the full case study](CASE_STUDY.md) and
[the architecture](ARCHITECTURE.md).

## Technology

- TypeScript and React
- Cloudflare Pages, Workers and D1
- Drizzle ORM with ordered migrations
- TPTS OneGate API V2 adapter
- Optional de-identified Google Gemini review advisory
- Cryptographically verified Cloudflare Access identity

## Delivery status

The platform is deployable and its internal workflows are functional.
Production payment rails still require the relevant provider credentials,
commercial activation, bank access and entity-specific integration agreements.
Nexus reports those boundaries explicitly instead of presenting inactive rails
as live.

---

Built for TPTS Financial Technology Group in Windhoek, Namibia.
