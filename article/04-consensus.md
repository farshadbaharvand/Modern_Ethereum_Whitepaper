# Consensus in Ethereum

Consensus is the mechanism by which Ethereum nodes agree on the canonical state of the blockchain. After Ethereum's Merge in September 2022, the network transitioned from **Proof of Work (PoW)** to **Proof of Stake (PoS)**, significantly improving energy efficiency and economic security.

---

## From PoW to PoS

| Consensus Mechanism | Status         | Description                                              |
|---------------------|----------------|----------------------------------------------------------|
| Proof of Work (PoW) | Legacy (pre-Merge) | Miners solved cryptographic puzzles to produce blocks   |
| Proof of Stake (PoS)| Current (post-Merge) | Validators propose and attest to blocks based on staked ETH |

The Merge replaced computational work with **economic commitment**, enabling sustainable consensus.

---

## How Proof of Stake (PoS) Works

In PoS, validators are randomly selected to propose new blocks and vote (attest) on their validity. This is coordinated by the **Beacon Chain**, Ethereum's consensus engine post-Merge.

### Key Concepts

| Concept        | Description |
|----------------|-------------|
| **Validator**  | A participant who stakes 32 ETH to help secure the network |
| **Slot**       | A 12-second interval in which one block can be proposed |
| **Epoch**      | A group of 32 slots (6.4 minutes) |
| **Attestation**| A validator’s vote on the head of the chain |
| **Finality**   | A block is finalized when it is agreed upon by ≥2/3 of validators |

---

## Beacon Chain and Validator Roles

The Beacon Chain manages validator duties and finality through a mechanism called **Casper FFG** (Friendly Finality Gadget).

### Validator Duties

- **Block Proposal**: One validator is chosen to propose a block every 12 seconds.
- **Attestation**: A committee of validators attests (votes) on the proposed block's validity and its place in the chain.

---

## Rewards and Penalties

Validators are incentivized with ETH rewards for correct behavior and penalized for faults or attacks.

| Action                  | Outcome          |
|-------------------------|------------------|
| Proposing a valid block | ✅ Reward        |
| Attesting correctly     | ✅ Reward        |
| Being offline/inactive  | ⚠️ Penalty       |
| Misbehavior (e.g. double voting) | ❌ Slashing |

---

## Slashing

Slashing is a penalty for malicious actions. It results in the forced exit of the validator and destruction of part of their stake.

### Slashable Offenses

- **Double Proposal**: Submitting two blocks for the same slot
- **Surround Voting**: Submitting conflicting votes that break safety rules

---

## Finality and Checkpoints

Ethereum uses **checkpoint finality** to ensure consensus:

1. **Epoch boundary blocks** are checkpoints.
2. A checkpoint becomes **justified** if ≥2/3 of validators attest to it.
3. Two consecutive justified checkpoints finalize the earlier one.

> Once finalized, a block cannot be reverted without slashing a third of validators.

---

## Ethereum PoS Consensus Diagram

![Ethereum PoS Consensus Diagram](./images/ethereum-consensus-diagram.png)

*This diagram shows validators proposing blocks, attesting, and forming finalized checkpoints through the Beacon Chain.*

---

## Client Stack: Post-Merge Architecture

Ethereum clients are now modular, separating **execution** and **consensus** responsibilities.

| Layer           | Client Type           | Examples                 |
|----------------|-----------------------|--------------------------|
| Consensus Layer| Beacon Chain Clients  | Prysm, Lighthouse, Teku  |
| Execution Layer| EVM Clients           | Geth, Nethermind, Besu   |

They communicate via the **Engine API** to coordinate state and block production.

---

## Validator Metrics (2025 Q2 Estimate)

| Metric                  | Value               |
|-------------------------|---------------------|
| Active Validators       | 1,200,000+          |
| Total ETH Staked        | ~40 million ETH     |
| Estimated APR           | ~3–5%               |
| Average Slashes/Month   | < 20                |

---

## Advantages of Proof of Stake

| Benefit             | Explanation |
|---------------------|-------------|
|  Energy Efficient | No mining hardware required |
|  Secure          | Attacks are costly and punishable |
|  Fast Finality    | Checkpoint finality every 6.4 minutes |
|  Decentralized    | Broader participation possible |
|  Modular Design   | Separation of execution and consensus |

---

## Conclusion

Ethereum's move to Proof of Stake fundamentally enhances its sustainability, security, and decentralization. Validators, not miners, now uphold the network by staking ETH and following protocol rules. The Beacon Chain coordinates all validator activity, ensuring the blockchain advances securely and efficiently.

