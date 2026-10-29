# Case study: from suspense to controlled financial operations

**TPTS Nexus — Namibian-born · Africa-ready.**

## Context

Public and enterprise collections often depend on a free-text bank reference as
the only link between incoming money and an account, invoice, permit, loan or
service. One typo can leave a valid payment unallocated, keep a payer in arrears
and send finance staff into a manual tracing loop. Lending operations add their
own disconnected processes: KYC review, affordability, credit decisions,
disbursement, mandates, repayment schedules, collections and arrears.

TPTS Nexus brings those flows into one governed system without requiring TPTS to
pretend that every external provider is already connected.

## Product thesis

African financial operations do not need another disconnected dashboard. They
need one control plane that can coordinate credit, collections, payment rails,
bank evidence and accounting truth while remaining honest about what is live in
each market. Nexus starts with Namibia and is designed to add entities,
currencies, products and reviewed providers without weakening the controls that
make the ledger trustworthy.

## The product

### Prevent reference errors

Nexus issues numeric, checksum-protected payment reference numbers and provides
server-side validation. Payment handoffs can carry the reference and amount so
the payer does not retype them.

### Detect and resolve what still slips through

The ClearLedger module imports bounded CSV or JSON statements, deduplicates
transactions and runs deterministic matching rules. Exact, well-supported
matches can progress; ambiguous, altered, duplicated, overpaid or
currency-mismatched items enter a controlled exception workflow.

### Originate and service credit

Operators can create masked customer records, complete KYC checks, configure
loan products, submit applications and record human credit decisions. Approved
applications create provisional schedules and pending-disbursement accounts.
Verified execution re-anchors the schedule to the actual bank booking date.

### Move money only from evidence

Treasury approval reserves configured liquidity but does not mark a
disbursement complete. A different authorised operator must select an exact,
one-use imported bank debit. Repayments similarly require an exact imported
credit or a successful, non-refunded OneGate credit. Allocations are persisted
in the deterministic order fee, interest, then principal.

### Keep providers honest

The connector catalogue distinguishes installed adapters, configuration
metadata and market support. Admins can register safe non-secret metadata,
enable or disable installed adapters, and run readiness tests that never send a
transaction. Metadata-only providers cannot be promoted into executable rails.

### Give operators one command centre

The Nexus cockpit turns portfolio, arrears, collections, liquidity and control
exceptions into work queues rather than decorative metrics. Actions appear only
when the same server-side eligibility rules can accept them, and blocked actions
explain the exact condition that must be resolved.

## Engineering outcomes

- Exact integer minor-unit money arithmetic.
- Request idempotency on financial mutations.
- Optimistic and transactional concurrency guards.
- Entity-scoped role and permission model.
- Maker-checker separation for allocation, posting and treasury decisions.
- One-use settlement-evidence claims.
- Immutable-style audit records for every material change.
- Bounded pagination and D1 statement/parameter budgets.
- Fail-closed Cloudflare Access authentication in production.
- Explicit synthetic-data and connector-readiness labels.

## End-to-end operating flow

1. A customer, KYC record, product and application are created under an entity.
2. A human credit decision produces a pending-disbursement loan and exact
   schedule.
3. Treasury maker and checker controls approve intent and reserve liquidity.
4. Exact imported bank evidence confirms execution and anchors the live
   schedule.
5. Mandates and repayment attempts remain separate from settlement truth.
6. Imported or authenticated provider evidence settles a repayment and applies
   fee, interest and principal in deterministic order.
7. Reconciliation, balances, portfolio state and audit history update together.

## Expansion model

Nexus is designed to grow through bounded additions rather than one-off forks:

- country and entity policies define local operating rules;
- connector readiness separates catalogue presence from executable capability;
- currency and money handling remain explicit at every boundary;
- product configuration changes terms without bypassing credit controls; and
- Google Gemini can provide optional de-identified review advisory, never an
  autonomous financial decision or a source of settlement truth.

## External activation boundary

Nexus can operate end to end with imported bank evidence. Live bank feeds, ERP
posting, notifications, card rails, instant EFT and other third-party providers
require their own credentials and agreements. Those are activation tasks, not
hidden application placeholders.

The protected demonstration uses synthetic records and may keep live-provider
actions disabled until the corresponding credentials, commercial activation
and access policies are in place. That is deliberate product behaviour, not a
simulated success state.

## Why it matters

The result is more than a payments dashboard or loan-management front end. It
is a single control plane in which intent, evidence, approval, settlement,
allocation, balances and audit history remain consistent across payment and
credit operations—and a foundation TPTS can take from Namibia to the rest of
Africa without trading speed for financial truth.
