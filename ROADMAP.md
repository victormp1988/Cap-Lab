# Cap Lab — Roadmap

## M0 — Project foundation

Establish:

- repository structure
- build system
- Java version
- testing conventions
- documentation
- CI foundation

## M1 — Portfolio accounting engine

Implement:

- instruments
- accounts
- transactions
- cash
- holdings
- cost basis
- FIFO
- realized P&L
- fees
- dividends
- FX conversions
- multi-currency
- fractional quantities
- deterministic reconstruction

**Status:** Initial milestone

## M2 — Historical portfolio state

Add:

- point-in-time portfolio snapshots
- historical holdings
- historical cash
- transaction timeline
- reproducible state reconstruction

## M3 — Market valuation

Add:

- market-price abstraction
- historical prices
- current valuation
- unrealized P&L
- price freshness and provenance

## M4 — Performance engine

Add:

- absolute return
- TWR
- MWR
- IRR
- annualized return
- drawdown
- contribution to return
- performance attribution

## M5 — Dividends and income analytics

Add:

- dividend history
- gross/net income
- withholding
- income by instrument
- income by account
- yield analytics

## M6 — Corporate actions

Add:

- stock splits
- reverse splits
- spin-offs
- mergers
- symbol changes
- other supported corporate actions

## M7 — Broker imports

Add broker adapters/import pipelines, initially considering:

- N26
- DEGIRO
- Interactive Brokers
- other brokers based on demand

Broker-specific formats must remain outside the accounting domain.

## M8 — Spanish tax engine

Add support for Spanish tax-oriented calculations, including:

- realized gains/losses
- FIFO tax lots where applicable
- dividends
- withholding
- deductible losses
- tax-year reporting

Legal/tax interpretation must be documented separately from mechanical calculations and validated against authoritative requirements.

## M9 — Portfolio analytics

Add:

- allocation
- country exposure
- sector exposure
- currency exposure
- broker/account exposure
- concentration
- contribution to returns
- risk metrics
- portfolio comparisons

## M10 — API

Expose portfolio capabilities through a stable API.

Potential technologies may be evaluated at this milestone rather than assumed in advance.

## M11 — Web application

Build the Cap Lab user interface for:

- portfolio overview
- positions
- transactions
- performance
- analytics
- dividends
- tax views
- configuration

## M12 — Production infrastructure

Add:

- authentication
- persistent database
- deployment
- observability
- backups
- security controls
- CI/CD

## M13 — Investment intelligence

Add structured support for:

- investment thesis
- valuation
- assumptions
- catalysts
- risks
- earnings
- thesis changes
- watchlists
- user-defined investment rules

## M14 — AI portfolio assistant

Add AI capabilities for:

- portfolio analysis
- thesis monitoring
- anomaly detection
- earnings interpretation
- research assistance
- user-defined alerts

AI must not silently modify accounting data.

## M15 — Production-grade platform

Harden the complete system for long-term use, including:

- reliability
- security
- data migration
- auditability
- scalability
- operational tooling

## Execution rule

Work on the earliest incomplete milestone.

After completing a milestone:

1. update this roadmap;
2. record material architectural decisions;
3. verify the Definition of Done;
4. proceed only when the active Goal permits continuing to the next milestone.
