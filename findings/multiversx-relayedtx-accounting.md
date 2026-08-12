# MultiversX: Relayed Transaction Accounting Asymmetry

## Overview

During security research of the MultiversX transaction execution engine, an accounting asymmetry was identified within the Relayed Transaction execution flow.

The issue originated from inconsistent balance-accounting behavior between multiple execution paths responsible for processing relayed transactions.

Under specific failure conditions, protocol state could diverge from expected accounting assumptions.

---

# System Context

MultiversX supports relayed transaction execution where one transaction can be responsible for executing another transaction on behalf of a user.

This creates multiple accounting domains:

- Outer transaction accounting
- Inner transaction accounting
- Fee accounting
- Balance reconciliation

Security depends on all accounting domains remaining synchronized regardless of execution outcome.

---

# Security Assumption

The protocol implicitly assumes:

> Every balance mutation applied during transaction execution is correctly reversed whenever execution fails.

This assumption must hold across every execution path.

Failure to maintain this property creates the possibility of accounting divergence.

---

# Root Cause

The vulnerability originated from asymmetric rollback behavior between execution paths.

Certain state updates were reverted when execution failed while corresponding balance mutations were not consistently reversed.

As a result:

1. Execution entered a failure path.
2. Partial state rollback occurred.
3. Accounting reconciliation became inconsistent.
4. Protocol assumptions were violated.

The issue was not caused by arithmetic errors.

Instead, it emerged from inconsistent state-management behavior between multiple execution branches.

---

# Impact

Successful exploitation could result in:

- Balance inconsistencies
- Accounting divergence
- Violation of protocol financial assumptions
- Unexpected value creation under specific execution scenarios

The vulnerability affected correctness of transaction accounting rather than availability.

---

# Discovery Process

The issue was discovered through:

## Transaction Flow Mapping

Execution paths were traced from transaction submission through final state commitment.

## State Transition Analysis

Each balance mutation was mapped against corresponding rollback logic.

## Failure Path Evaluation

Special attention was given to:

- Reverts
- Partial failures
- Nested transaction execution
- Accounting reconciliation

## Verification

Custom integration tests were constructed to validate the hypothesis and reproduce the accounting divergence.

---

# Security Lessons

Several important lessons emerged from this research:

### Accounting Must Be Symmetric

Every balance mutation requires a corresponding rollback path.

### Failure Paths Are Security Critical

Attackers frequently target exceptional execution paths rather than intended flows.

### State Consistency Is Global

Local correctness does not guarantee global correctness.

### Execution Boundaries Are Dangerous

Security assumptions often fail where responsibility transitions between components.

---

# Skills Demonstrated

- Blockchain Security Research
- State Accounting Analysis
- Transaction Lifecycle Analysis
- Invariant Verification
- Integration Test Development
- Root Cause Analysis
- Go Code Review
