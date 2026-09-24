# Cap Lab

Cap Lab is an investment portfolio management and analytics platform.

The long-term goal is to provide a complete system for:

- portfolio accounting
- performance analysis
- dividends and income
- broker imports
- tax calculations
- portfolio analytics
- investment intelligence
- AI-assisted analysis

## Current milestone

**M1 — Portfolio Accounting Engine**

The first implementation focuses on a deterministic accounting core that can reconstruct portfolio state from chronological transactions.

It supports:

- stocks and ETFs
- multiple accounts
- multiple currencies
- fractional quantities
- deposits and withdrawals
- buys and sells
- fees
- dividends
- FX conversions
- FIFO cost basis
- realized P&L

## Design principles

### Financial correctness first

Accounting calculations must be deterministic, auditable, and tested.

### Domain isolation

The core accounting model should not depend on UI, HTTP, databases, brokers, or external market data.

### Transaction history as source of truth

Portfolio state should be reproducible from the transaction history.

### Incremental delivery

Build the accounting foundation before adding analytics, integrations, tax functionality, or AI.

## Repository structure

The exact package structure is determined during implementation, but the intended separation is:

- domain
- application
- infrastructure

## Testing

Every accounting rule should have automated tests, including edge cases and invalid operations.

## License

To be determined.
