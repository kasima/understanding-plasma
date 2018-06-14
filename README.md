# Understanding Plasma, A Series

## Outline

- [Preface](0-preface.md)
- [Introduction](1-introduction.md)
- Basic concepts
  - [Merkle Trees](basic_concepts/merkle_tree.md)
  - UTXOs
  - RLP
  - ...
- How Plasma Works (happy paths)
  - Root chain
  - Child chain
  - New transactions
  - Exits
- Faults and Mitigations (sad paths)
  - Block witholding
  - Faulty Exits
  - Invalid child block
  - ...
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
