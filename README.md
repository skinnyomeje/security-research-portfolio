# Security Research Portfolio

Hi, I'm Skinnee Omeje.

Smart Contract Auditor and Blockchain Security Researcher focused on smart contract, protocol, and infrastructure security.

---

## About Me

I perform manual security reviews of blockchain protocols, smart contracts, and validator infrastructure across multiple ecosystems.

My work focuses on:

- Smart Contract Security
- Protocol Logic Analysis
- State Accounting Vulnerabilities
- Consensus & Validator Systems
- Race Conditions & Concurrency Bugs
- Economic Security
- Proof-of-Concept Development

---

## Technical Stack

### Languages

- Solidity
- Rust
- Go
- Motoko
- C

### Ecosystems

- Ethereum
- Solana
- Internet Computer (ICP)
- MultiversX

### Tools

- Foundry
- Hardhat
- Anchor
- Forge
- Git
- Docker

---

# Security Research

## WaterNeuron Bug Bounty

### Summary

Discovered a protocol accounting vulnerability affecting withdrawal cancellation logic within WaterNeuron's liquid staking system.

### Impact

- Exchange rate invariant violation
- Incorrect accounting state transitions
- Potential protocol fund imbalance

### Status

Verified and reported through bug bounty process.

---

## CrumbEatr Private Audit

### Scope

Independent security review of the CRUMBEATR protocol.

### Areas Reviewed

- Governance controls
- Token accounting
- Business logic
- Privileged operations
- Economic attack surfaces

### Results

Identified multiple vulnerabilities across different severity levels and produced a complete audit report.

---

## MultiversX Security Research

### Summary

Performed security analysis of MultiversX transaction execution and relayed transaction processing.

### Findings

Identified an asymmetric rollback vulnerability capable of creating accounting inconsistencies between transaction execution paths.

### Verification

Built proof-of-concept integration tests to demonstrate exploitability.

---

# Development Projects

## Solana Staking Vault

Rust-based Solana staking vault developed to study:

- Anchor framework
- Program Derived Addresses (PDAs)
- SPL Token interactions
- Transaction processing
- Local validator testing

Repository:
https://github.com/skinnyomeje/staking_vault

---

# Technical Writing

## Understanding C Memory and Pointers

Explores:

- Stack vs Heap
- Memory segmentation
- Pointer fundamentals
- Program memory layout

---

## Rust Borrowing

Explains:

- Ownership
- Borrowing
- References
- Memory safety guarantees

---

## Solana Virtual Machine (SVM)

Deep dive into:

- Solana execution model
- Parallel transaction execution
- Runtime architecture
- Scalability design

---

# Audit Methodology

My typical review process:

1. Recon
2. Map
3. Demystify
4. Hunt
5. Verify
6. Report

Focus is placed on understanding protocol invariants before attempting vulnerability discovery.

---

# Contact

LinkedIn:
www.linkedin.com/in/skinnee-omeje-46b505235

Medium:
https://medium.com/@SkinneeOmeje

GitHub:
https://github.com/skinnyomeje
