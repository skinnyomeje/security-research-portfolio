# Security Audit Methodology

## Introduction

This document outlines the methodology I use when performing smart contract audits, protocol reviews, and blockchain infrastructure assessments.

The objective of this process is not simply to identify vulnerabilities, but to develop a complete understanding of how a system is intended to operate before evaluating how it can fail.

The methodology is built around six phases:

1. Recon
2. Map
3. Demystify
4. Hunt
5. Verify
6. Report

Each phase progressively reduces uncertainty and increases confidence in both vulnerability discovery and vulnerability validation.

---

# Phase 1: Recon

## Objective

Develop a high-level understanding of the system before reviewing implementation details.

Many vulnerabilities are missed because reviewers begin reading code before understanding the protocol itself.

Recon focuses on understanding:

- Protocol purpose
- User workflows
- Asset movement
- Trust assumptions
- Administrative controls
- Security boundaries
- External dependencies

## Questions

During Recon, I attempt to answer:

- What problem does the protocol solve?
- Who are the participants?
- What assets are being protected?
- What assumptions does the protocol make?
- Who can influence protocol state?

## Deliverables

The output of this phase is a protocol-level mental model.

At this stage, implementation details are intentionally ignored.

---

# Phase 2: Map

## Objective

Transform protocol understanding into an attack-surface map.

The purpose of mapping is to identify every location where protocol state can change.

## Areas Mapped

### Entry Points

Functions callable by:

- Users
- Administrators
- External contracts
- Off-chain services

### State Mutations

Locations where protocol state is modified.

### Asset Flows

Movement of:

- Tokens
- Rewards
- Deposits
- Withdrawals
- Fees

### Privileged Operations

Functions requiring elevated permissions.

### External Dependencies

Interactions with:

- Oracles
- Validators
- Bridges
- External contracts
- Third-party systems

## Deliverables

A complete attack-surface inventory.

---

# Phase 3: Demystify

## Objective

Reduce protocol complexity into a collection of security assumptions.

Many systems appear complex because implementation details obscure their underlying invariants.

The goal is to identify:

- What must always be true
- What must never happen
- What assumptions the protocol depends on

## Invariant Identification

Examples include:

### Accounting Invariants

Total assets must equal total liabilities.

### Ownership Invariants

Users cannot control assets belonging to others.

### Authorization Invariants

Privileged operations must remain restricted.

### Economic Invariants

Rewards cannot exceed available value.

### State Invariants

State transitions must remain internally consistent.

## Deliverables

A list of protocol invariants and security assumptions.

This phase often determines where vulnerabilities are eventually discovered.

---

# Phase 4: Hunt

## Objective

Actively search for violations of identified assumptions.

Rather than reviewing code line-by-line without direction, hunting focuses on finding situations where protocol assumptions can fail.

## Common Hunting Categories

### Access Control

Questions:

- Can permissions be bypassed?
- Can authority be escalated?

### State Accounting

Questions:

- Can balances become inconsistent?
- Can accounting diverge from reality?

### State Transitions

Questions:

- Can protocol state become invalid?
- Can transitions occur out of order?

### Economic Security

Questions:

- Can incentives be manipulated?
- Can value be created unexpectedly?

### Concurrency

Questions:

- Can shared state be modified unexpectedly?
- Can execution order influence security?

### Edge Cases

Questions:

- What happens during failures?
- What happens during cancellation?
- What happens during partial execution?

## Deliverables

Potential vulnerabilities requiring validation.

---

# Phase 5: Verify

## Objective

Determine whether a suspected issue represents a genuine vulnerability.

Many observations appear dangerous but cannot actually be exploited.

Verification separates theoretical concerns from real security issues.

## Verification Process

### Root Cause Analysis

Identify why the issue exists.

### Reachability Analysis

Determine whether an attacker can reach the vulnerable state.

### Exploitability Analysis

Determine whether protocol assumptions can actually be violated.

### Impact Analysis

Determine consequences if exploitation succeeds.

### Proof of Concept Development

Where appropriate:

- Unit tests
- Integration tests
- Reproduction steps
- Transaction sequences

## Deliverables

Confirmed vulnerabilities with demonstrated impact.

---

# Phase 6: Report

## Objective

Communicate findings clearly enough that they can be understood, reproduced, and fixed.

A vulnerability is not complete until it can be explained.

## Reporting Principles

### Accuracy

Every claim must be supported by evidence.

### Reproducibility

Engineers should be able to reproduce the issue.

### Root Cause Focus

Reports should explain why the vulnerability exists.

### Impact Clarity

Reports should explain what an attacker gains.

### Remediation Guidance

Reports should provide actionable recommendations.

## Deliverables

Final audit findings.

---

# Core Principles

The following principles guide every review.

## Understand Before Auditing

Protocol understanding precedes code review.

## Invariants First

Security assumptions are often more important than individual functions.

## Follow State

Vulnerabilities frequently emerge where protocol state changes.

## Follow Value

Asset movement often reveals hidden attack surfaces.

## Exceptional Paths Matter

Failures, cancellations, and edge cases frequently contain vulnerabilities.

## Verify Everything

Suspicion is not evidence.

Every finding must be validated before reporting.

---

# Workflow Summary

Recon
→ Understand the protocol

Map
→ Identify the attack surface

Demystify
→ Extract assumptions and invariants

Hunt
→ Search for assumption violations

Verify
→ Confirm exploitability and impact

Report
→ Communicate findings clearly

This methodology is designed to provide a structured and repeatable approach to identifying vulnerabilities across smart contracts, blockchain protocols, and distributed systems.
