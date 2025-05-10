# Smart Contracts on Ethereum

Smart contracts are the foundational innovation that makes Ethereum a programmable blockchain. They enable decentralized applications (dApps), autonomous organizations, token standards, and a wide range of trustless interactions.

---

## Definition and Historical Background

A **smart contract** is a self-executing piece of code deployed on the blockchain that automatically enforces the terms of an agreement or process without requiring a third party.

The concept was first introduced by **Nick Szabo** in the 1990s, but Ethereum was the first platform to implement smart contracts in a Turing-complete environment.

| Key Milestones |
|----------------|
| 1994 – Nick Szabo coins the term "smart contract" |
| 2013 – Vitalik Buterin proposes Ethereum |
| 2015 – Ethereum mainnet launches with smart contract support |
| 2017+ – ERC-20, ICO boom, DeFi, NFTs and DAOs powered by smart contracts |

---

## How Smart Contracts Work on Ethereum

Smart contracts are deployed to the Ethereum blockchain and executed by the **Ethereum Virtual Machine (EVM)**. They reside at an address and can store state, receive ETH, and interact with other contracts.

### Key Components:

| Component             | Description |
|------------------------|-------------|
| **EVM**               | Executes smart contract bytecode deterministically |
| **Solidity**          | The most popular high-level language for writing contracts |
| **Opcodes**           | Low-level machine instructions executed by the EVM |
| **ABI (Application Binary Interface)** | Specifies how to interact with compiled contracts |
| **Storage**           | Persistent state maintained on-chain |

---

## Deployment Process

1. Write the contract in **Solidity**.
2. Compile to **EVM bytecode** and generate ABI.
3. Use a wallet (e.g., MetaMask) or framework (e.g., Hardhat, Foundry) to deploy.
4. Pay **gas fees** based on the complexity and size of the contract.

### Example Solidity Contract

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract SimpleStorage {
    uint public storedData;

    function set(uint x) public {
        storedData = x;
    }

    function get() public view returns (uint) {
        return storedData;
    }
}
