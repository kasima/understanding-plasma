# Introduction

## What is Plasma?

The [whitepaper](http://plasma.io/plasma.pdf), written by Vitalik Buterin and Joseph Poon, describes Plasma as:

> Plasma is a proposed framework for incentivized and enforced execution of smart contracts which is scalable to a significant amount of state updates per second (potentially billions) enabling the blockchain to be able to represent a significant amount of decentralized financial applications worldwide.

That's a lot to digest. More simply, Plasma is a method of securely scaling a blockchain. It's not a framework like _Ruby on Rails_, _Express.js_, or _UIKit_. I think about it as a proposed [design pattern](https://en.wikipedia.org/wiki/Software_design_pattern) to allow a blockchain to represent a lot more state updates (transactions).


## Under Construction

Plasma is currently under heavy research and development by OmiseGO and multiple teams around the world. The white paper specifies many concepts that are yet to be explored for implementation. In the [Specifications](specifications) section, you can see more concrete specifications of Plasma, as well as implementations of those specs.


## Structure

In the most general case, Plasma describes the interaction of a tree of blockchains.

[ XXX - add graphic ]

Doing a depth-first traversal of the tree, each chain periodically submits a summary update of its state to the parent chain. Eventually, the update of all the updates get submitted to a root chain (e.g. Ethereum).

By doing this, we extend the security of the root chain to the entire structure of blockchains. The blockchains that are the children of the root can operate concurrently and :boom:, billions of transactions per second. Easy!

I know I'm being pretty hand wavy about all of this right now. Don't worry, I'll get into detail in the following posts. All you really need to know right now is...

[ XXX - yo dawg graphic ]


## Root Chain

Plasma is blockchain agnostic for its root chain. The purpose of the root chain is to secure the entire Plasma structure. It's a design pattern that can be implemented on any blockchain that can support the interaction between a first-level child chain and the root chain.

Given that the implementation and design details of Plasma are currently under active research by multiple teams, the protocol between a child chain and root chain is in flux. Since it's in flux, we need a root chain that can support a changing protocol and that means using a root chain that can support smart contracts.

At OmiseGO and for the rest of these posts, we'll be using Ethereum as our root chain. That means we'll be using Solidity as our smart contract language in the examples.


## Plasma Chain

All the blockchains that are children of the root are called _Plasma chains_. Each Plasma chain will operate as a child and potentially as a parent too, depending on whether it's a an internal node or leaf in the tree.

### As a child chain

The Plasma chain acts as a child by periodically reporting an update back to its parent chain (which can also the be the root chain). This update needs to be able to prove inclusion of the data in the child chain. For many of the Plasma specifications so far (e.g. Plasma MVP), this magical update up to the parent chain takes the form of the _Merkle root of a Merkle tree of transactions_ from the most recent block of the child chain.

[Take a dive into how Merkle trees work and how they're used in Plasma.](basic_concepts/merkle_tree.md)

### As a parent chain

The Plasma chain can act as a parent chain just like the root chain. It offers the same functionality as the root chain. For practical reasons, it does not have to support the exact same protocol (e.g. Ethereum ABI calls). Each parent-child chain's protocol is up to that pair.


## Summary

Plasma is a design pattern for scaling the rate of state changes a blockchain can represent. It does this by organizing multiple blockchains into a tree structure, with a specific interaction between parent and child chain. By doing this, we can extend the security of the root chain down over the entire Plasma structure, while allowing the child chains to operate concurrently.

The specifics of how the chains interact is fundamental to the security of the structure. We'll cover all of that in depth.
