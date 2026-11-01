# TPTS Nexus architecture

**Namibian-born · Africa-ready.** The architecture separates market-specific
activation from the financial controls that must remain invariant everywhere.

```mermaid
flowchart LR
  subgraph channels[Payment, collection and reference channels]
    BANK[Bank statements]
    ONE[TPTS OneGate]
    LINK[Hosted payment handoff]
    FXFEEDS[Reviewed FX reference feeds]
    FUTURE[Reviewed future connectors]
  end

  subgraph edge[Trusted application boundary]
    ACCESS[Cloudflare Access]
    API[Typed API and idempotency controls]
    CONNECT[Connector lifecycle guard]
  end

  subgraph nexus[TPTS Nexus]
    ORIG[Origination and KYC]
    LOANS[Loan accounts and schedules]
    COLLECT[Mandates and collections]
    TREASURY[Treasury maker-checker]
    LEDGER[ClearLedger reconciliation]
    FX[FX reference desk]
    RISK[Risk and portfolio cockpit]
    ADMIN[Administration and audit]
  end

  subgraph policy[Market and entity policy]
    ENTITY[Entity boundary]
    CURRENCY[Currency and money rules]
    PRODUCT[Credit product rules]
    RAILS[Approved provider availability]
  end

  subgraph data[Cloudflare data plane]
    D1[(D1 operational ledger)]
    EVIDENCE[(One-use evidence claims)]
    AUDIT[(Audit events)]
  end

  BANK --> CONNECT
  ONE --> CONNECT
  LINK --> CONNECT
  FXFEEDS --> API
  FUTURE -. metadata until adapter exists .-> CONNECT
  ACCESS --> API
  CONNECT --> API
  ENTITY --> API
  CURRENCY --> API
  PRODUCT --> API
  RAILS --> CONNECT
  API --> ORIG
  API --> COLLECT
  API --> TREASURY
  API --> LEDGER
  API --> FX
  ORIG --> LOANS
  LOANS --> COLLECT
  TREASURY --> EVIDENCE
  COLLECT --> EVIDENCE
  LEDGER --> EVIDENCE
  ORIG --> D1
  LOANS --> D1
  COLLECT --> D1
  TREASURY --> D1
  LEDGER --> D1
  FX --> D1
  D1 --> RISK
  D1 --> ADMIN
  API --> AUDIT
```

## Trust boundaries

1. Identity is verified before application membership and permissions are
   evaluated.
2. Connector lifecycle state is enforced in both the interface and server
   route; the server remains authoritative.
3. A provider return URL never proves settlement.
4. Imported or provider evidence must match amount, currency, direction,
   timing and unclaimed status.
5. Evidence, balances, schedules, liquidity, operation status and audit records
   commit atomically.
6. FX reference rates are indicative only and never authorise a debit,
   settlement, posting, refund or provider instruction.
7. The public case study contains no private source or runtime configuration.

## Invariants and adaptable layers

| Invariant control | Market-adaptable layer |
| --- | --- |
| Authenticated identity and scoped permissions | Entity membership and local roles |
| Integer minor-unit money arithmetic | Currency and display conventions |
| Maker-checker separation | Approval thresholds and policies |
| Provider or bank evidence for settlement | Activated rails and bank formats |
| Separation of reference FX from execution quotes | Reviewed rate providers and display pairs |
| Idempotent financial mutations | Product and workflow configuration |
| Atomic ledger and audit updates | Country-specific reporting integrations |

This separation lets TPTS expand without copying the platform into divergent
country editions or weakening the evidence chain.
