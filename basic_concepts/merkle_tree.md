# Merkle Trees

[Merkle Trees](https://en.wikipedia.org/wiki/Merkle_tree), or Hash Trees, are trees (usually binary) of hashes starting with hashing the data at the leaf nodes. The hashes are hashed together up the tree until we reach a single root hash, also called the Merkle Root.

[ XXX - graphic of full merkle tree – used below as well ]

[ XXX - code to build a bninary merkle tree ]


## Properties

Merkle trees allow you to verify data at a leaf node efficiently.

Say you have the root hash. To verify the data at a leaf node provided to you, you only need the sibling hashes of the branch path to get to the root:

[ XXX - graphic of data needed to verify leaf ]

[ XXX - code to verify data ]

The set of sibling hashes needed to verify the data is called a _proof_.

The cool part of a Merkle tree is that the time it takes to verify a node in set of data grows logarithmically to number of items in the set – for binary merkle trees, it's O(log[base-2] n).


## Application in Plasma

The Merkle root hash of all the transactions in a Plasma block is what gets submitted periodically to the root/parent chain. This root is used to verify that a transaction exists when a participant in the Plasma chain wants to exit their state (funds).

The exit happens when a participant submits the transaction with the value they're trying to exit along with the proof to the root/parent contract. The contract verifies that the transaction actually existed in the child chain by comparing the transaction data and proof to the Merkle root that was submitted previously by the child chain.

Once the transaction is verified, it eligible for exit. You can see concrete details in the [plasma-mvp implementation](implementations/plasma-mvp#exits).
