# Cap Lab — Product Specification

## 1. Product objective

Cap Lab is an investment portfolio management and analytics platform.

The first milestone establishes a deterministic portfolio accounting engine capable of reconstructing portfolio state from chronological financial transactions.

The initial engine must correctly calculate:

- holdings
- cash balances
- cost basis
- realized profit and loss
- transaction-level effects

The accounting engine is the foundation for later performance, tax, analytics, broker-import, and investment-intelligence capabilities.

## 2. Initial technology

For M1:

- Java
- Gradle
- a modern LTS Java version
- JUnit

Use a clean separation between domain, application, and infrastructure concerns.

Do not introduce a database, HTTP server, frontend, or external market-data dependency for M1 unless technically necessary for the core engine.

## 3. Asset types

M1 supports:

- Stock
- ETF

The model should allow future instrument types without requiring a redesign of the accounting core.

Each instrument should have at least:

- stable identifier
- symbol
- name
- asset type
- trading currency

## 4. Accounts

A portfolio may contain multiple accounts.

Each account has:

- stable identifier
- name
- base currency

Transactions must identify their account.

## 5. Transactions

M1 supports:

- BUY
- SELL
- DEPOSIT
- WITHDRAWAL
- FEE
- DIVIDEND
- FX_CONVERSION

Transactions must contain enough information to deterministically reconstruct the portfolio.

Transaction ordering must be deterministic using timestamp plus a unique transaction identifier.

## 6. Money and quantities

Monetary values must use decimal arithmetic rather than binary floating point.

Fractional shares are supported.

Quantity and price precision must be explicit and testable.

Currency must be represented explicitly wherever monetary amounts are involved.

## 7. Portfolio reconstruction

Given an empty initial state and an ordered list of valid transactions, Cap Lab must deterministically reconstruct:

- cash by account and currency
- instrument quantities
- cost basis
- realized P&L
- transaction effects

Replaying the same ordered transaction set must produce the same state.

## 8. FIFO cost basis

M1 uses FIFO for initial cost-basis accounting.

Example:

- Buy 10 shares at €100
- Buy 10 shares at €120
- Sell 15 shares at €150

The sale consumes:

- 10 shares from the €100 lot
- 5 shares from the €120 lot

Remaining position:

- 5 shares at €120 cost basis

Realized P&L must be calculated from the consumed lots and the sale proceeds, with fees incorporated according to the defined accounting model.

## 9. Realized P&L

The engine must calculate realized P&L for sales using the configured cost-basis method.

At minimum, the result must expose:

- quantity sold
- proceeds
- consumed cost basis
- fees attributable to the transaction
- realized P&L

## 10. Unrealized P&L

M1 defines the data model needed to represent unrealized P&L, but does not retrieve external market prices.

Market valuation is a later milestone.

## 11. Multi-currency

M1 supports multiple currencies, including EUR and USD.

Currency conversion must be represented explicitly rather than inferred.

The accounting engine must preserve the original currency of transactions and balances.

## 12. Validation

The engine must reject invalid operations explicitly.

Examples include:

- selling more shares than available
- withdrawing more cash than available where the account policy forbids it
- invalid quantities
- invalid monetary values
- missing currencies
- malformed instruments
- ambiguous transaction ordering

Error behavior must be deterministic and covered by tests.

## 13. Idempotency and determinism

Transaction identifiers must support safe identification of repeated input.

The system must not silently apply the same transaction twice when the application layer guarantees idempotent ingestion.

Given the same transaction set and ordering, reconstruction must always produce the same result.

## 14. Deterministic example dataset

Create a small deterministic dataset covering at least:

- cash deposit
- stock purchase
- second purchase of the same stock
- partial sale using FIFO
- dividend
- fee
- cash withdrawal
- EUR transaction
- USD transaction
- fractional shares

Document the expected final state.

## 15. Out of scope for M1

Do not implement:

- authentication
- web UI
- external broker APIs
- CSV imports
- external market data
- tax forms
- Spanish tax rules
- corporate actions
- options
- futures
- crypto
- portfolio optimization
- AI recommendations
- notifications

These belong to later milestones.

## 16. M1 Definition of Done

M1 is complete when:

1. The project builds successfully.
2. The accounting domain is implemented.
3. All M1 transaction types are supported.
4. FIFO cost basis is implemented.
5. Realized P&L is implemented.
6. Multi-account and multi-currency behavior is covered.
7. Fractional quantities are supported.
8. Invalid operations are rejected deterministically.
9. A deterministic example dataset exists with expected results.
10. Comprehensive automated tests pass.
11. Documentation reflects the actual implementation.
12. No external market-data or broker dependency is required.
