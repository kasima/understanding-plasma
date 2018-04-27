# Understanding Plasma, A Series

## Outline

- Introduction
- Basic concepts
  - Merkle Trees
  - UTXOs
  - RLP
- How Plasma Works (happy paths)
  - Root chain
  - Child chain
  - New transactions
  - Exits
- Faults and Mitigations (sad paths)
  - Block witholding
  - Double spends
- Specifications
  - Plasma MVP
    - Single child chain
    - 2 inputs / 2 outputs
    - 14 day exit window
  - Plasma Cash
    - non-fungible
    - no confirmations
- Implementations
  - omisego/plasma-mvp
  - omisego/plasma-cash
