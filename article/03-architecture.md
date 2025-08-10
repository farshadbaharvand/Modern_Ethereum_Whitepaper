#  03. Ethereum Architecture

Ethereum is a decentralized, programmable blockchain platform. Its architecture is designed to support trustless computation via smart contracts, while maintaining a secure, consensus-driven, and globally distributed network. At its core, Ethereum consists of various layers and components that work together to execute, validate, and store decentralized applications (dApps).

---

## High-Level Architecture Overview

The architecture of Ethereum can be conceptually divided into the following layers:

1. **Networking Layer** – Peer-to-peer communication
2. **Consensus Layer** – Agreement on the state of the blockchain
3. **Execution Layer** – Running transactions and smart contracts
4. **Data Layer** – Storage of blockchain data
5. **Application Layer** – Interfaces for users and developers

---

## 1. Networking Layer

- Responsible for peer discovery and message propagation.
- Implements the Ethereum Wire Protocol (devp2p).
- Uses a **gossip protocol** to propagate transactions, blocks, and state changes.

### Key Features:
| Component     | Role                            |
|--------------|---------------------------------|
| devp2p        | Ethereum's P2P messaging protocol |
| Libp2p (in future) | Modular networking stack for Ethereum clients |
| Node Discovery Protocol | Finds peers dynamically |

---

## 2. Consensus Layer

- Ethereum now uses **Proof of Stake (PoS)** via the **Beacon Chain**, replacing Proof of Work in the Merge (2022).
- This layer coordinates validator responsibilities: proposing blocks, attesting to blocks, and finalizing checkpoints.

### Key Components:
| Element        | Description |
|----------------|-------------|
| Beacon Chain   | Coordinates validators and randomness |
| Validators     | Stake ETH and propose/attest blocks |
| Finality Gadget | Ensures block finality via Casper FFG |

---

## 3. Execution Layer

- Executes transactions and smart contracts using the **Ethereum Virtual Machine (EVM)**.
- Maintains the current **state** of all accounts, contracts, balances, and storage.

### Key Concepts:

| Element       | Description |
|---------------|-------------|
| EVM           | A stack-based virtual machine for deterministic computation |
| Transactions  | Include contract creation, execution, transfers |
| Gas           | Limits computation and prevents DoS attacks |
| State Trie    | A Merkle Patricia Trie storing current state |

---

## 4. Data Layer

- Stores blockchain history, receipts, and state information.
- Uses **Merkle Patricia Tries** to store state, transactions, and receipts securely and verifiably.

### Structure:

| Trie Type         | Contents                        |
|-------------------|----------------------------------|
| State Trie        | Account states and balances      |
| Transaction Trie  | All transactions per block       |
| Receipt Trie      | Logs and gas usage for each tx   |

This trie-based structure enables **light clients** and **zero-knowledge proofs** for verifiable state queries.

---

## 5. Application Layer

- Exposes Ethereum’s functionality to users and developers through smart contracts, wallets, and dApps.

### Interfaces:

| Component     | Description |
|---------------|-------------|
| Smart Contracts | On-chain logic that executes automatically |
| JSON-RPC API    | Interface used by wallets and dApps |
| Wallets (e.g., MetaMask) | Allow users to sign and send transactions |
| dApps           | Decentralized applications running on Ethereum |

---

## Client Architecture

Ethereum has multiple client implementations written in different languages (Geth, Nethermind, Prysm, Lighthouse). A client is split into two major stacks:

| Stack             | Function                         |
|------------------|----------------------------------|
| Execution Client | Manages state and executes EVM   |
| Consensus Client | Handles PoS consensus and Beacon Chain |

They communicate via the **Engine API** post-Merge.

---

## Post-Merge Architecture (Execution + Consensus Split)

With the Merge complete:

- **Execution Clients**: Handle transactions and EVM execution (e.g., Geth, Nethermind).
- **Consensus Clients**: Handle PoS validator duties and finality (e.g., Lighthouse, Prysm).

Both are required for a full Ethereum node.

---

## Summary Table

| Layer             | Responsibilities                                       |
|------------------|--------------------------------------------------------|
| Networking        | Peer discovery, message propagation                   |
| Consensus         | Finality, block validation, validator coordination    |
| Execution         | Transaction execution, smart contracts, EVM           |
| Data              | Blockchain state, receipts, Merkle trees              |
| Application       | Wallets, dApps, external interfaces                   |

---

## Conclusion

Ethereum’s architecture is modular, extensible, and purpose-built for a decentralized future. By separating concerns across networking, consensus, and execution layers, Ethereum ensures both scalability and resilience while supporting innovation at the application layer.

