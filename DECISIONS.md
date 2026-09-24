# Cap Lab — Architectural Decisions

## ADR-001 — Keep the accounting core framework-independent

**Decision:** The accounting domain must not depend directly on HTTP, UI, database, broker, or market-data technologies.

**Reason:** Financial correctness and deterministic reconstruction are easier to test and evolve when the domain is isolated.

## ADR-002 — FIFO is the initial cost-basis method

**Decision:** M1 uses FIFO.

**Reason:** FIFO provides deterministic lot consumption and establishes the accounting foundation for later tax and analytics functionality.

Alternative methods may be introduced later without changing the transaction ingestion model.

## ADR-003 — Support fractional quantities

**Decision:** Instrument quantities may be fractional.

**Reason:** Modern brokers support fractional shares and real portfolios may contain them.

## ADR-004 — Use decimal arithmetic

**Decision:** Monetary calculations must use decimal arithmetic and explicit rounding.

**Reason:** Binary floating-point arithmetic is inappropriate for deterministic financial accounting.

## ADR-005 — Transaction history is the source of truth

**Decision:** Portfolio state is reconstructed from the transaction history rather than treating mutable position snapshots as the authoritative record.

**Reason:** This provides auditability, reproducibility, and deterministic reconstruction.

## ADR-006 — Broker formats stay outside the domain

**Decision:** Broker-specific CSV/API formats must be translated into Cap Lab transactions at an infrastructure boundary.

**Reason:** The accounting model should not become coupled to individual brokers.

## ADR-007 — External market data stays outside M1

**Decision:** The first accounting engine does not depend on external price providers.

**Reason:** Accounting correctness should be testable without network access or changing market data.

## ADR-008 — AI cannot silently modify accounting data

**Decision:** Future AI functionality may analyze and propose changes but must not silently mutate transactions, holdings, or accounting results.

**Reason:** Financial data requires explicit auditability and user control.
