# WaterNeuron: Exchange Rate Invariant Violation

## Overview

During security research of WaterNeuron's liquid staking architecture, a protocol-level accounting issue was identified affecting exchange-rate consistency.

The issue originated from a state transition that allowed protocol accounting assumptions to become inconsistent following a withdrawal-cancellation workflow.

---

# System Context

WaterNeuron maintains an exchange-rate relationship between:

- Deposited assets
- Staking positions
- Liquid staking representations
- Withdrawal accounting state

Protocol correctness depends on preservation of exchange-rate invariants across every state transition.

---

# Security Assumption

The protocol assumes:

> Exchange-rate calculations remain consistent regardless of the sequence of valid user operations.

This assumption must hold for:

- Deposits
- Withdrawals
- Reward distribution
- Withdrawal cancellation

Any state transition capable of violating this assumption introduces protocol risk.

---

# Root Cause

The vulnerability originated from an interaction between withdrawal processing and withdrawal cancellation logic.

A valid sequence of operations could cause protocol accounting state to diverge from the assumptions used during exchange-rate calculation.

The issue was not caused by incorrect mathematical formulas.

Instead, the root cause was a mismatch between expected and actual state transitions.

---

# Impact

Violation of exchange-rate invariants can produce:

- Accounting inconsistencies
- Incorrect asset representation
- Distorted protocol state
- Unexpected economic outcomes

The severity of invariant violations stems from their ability to undermine assumptions relied upon by multiple protocol components simultaneously.

---

# Discovery Process

The issue was discovered through:

## Invariant Identification

Core protocol assumptions were documented before code review began.

## State Transition Mapping

Each operation capable of modifying protocol accounting state was analyzed.

## Edge Case Evaluation

Special attention was given to:

- Partial completion scenarios
- Cancellation paths
- Repeated state transitions
- Sequence-dependent behavior

## Verification

The hypothesis was validated by constructing execution sequences capable of producing invariant violations.

---

# Security Lessons

Several recurring security principles were reinforced:

### Invariants Matter More Than Functions

Individual functions may behave correctly while the protocol remains vulnerable.

### Cancellation Logic Is High Risk

Cancellation paths often receive less scrutiny than primary execution flows.

### Sequence Matters

Security analysis must consider operation ordering rather than isolated transactions.

### Protocol State Is Interconnected

Accounting assumptions frequently span multiple independent components.

---

# Skills Demonstrated

- Protocol Security Research
- Invariant Analysis
- Economic Security Review
- State Transition Auditing
- Root Cause Analysis
- Vulnerability Verification
- Internet Computer Security
