# **ERI‑NP1‑001 — NovaPay: Economic Admissibility via Pre‑Execution Control**

**Status:** Candidate ERI  
**Version:** 1.0  
**Conforms to:** **ERI‑000 (Executable Reference Implementation Formalization v1.1)**

***

## 0. Normative Keywords (Normative)

The keywords **MUST**, **MUST NOT**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are to be interpreted as normative requirements.

***

## 1. ERI Identity Card (Normative)

*   **ERI ID:** ERI‑NP1‑001
*   **ERI Name:** NovaPay — Economic Admissibility Execution
*   **Domain:** Economic and Resource‑Bound Execution
*   **Decision Boundary:** Pre‑Execution Admissibility Gate
*   **Release Point:** Release Boundary (RB) — atomic commit point
*   **Conformance Claim:** ERI‑000

### 1.1 Normative Rule (Normative)

If this implementation violates any ERI principle marked **MUST** in **ERI‑000**, it **SHALL NOT** be presented as an ERI.

***

## Part I — ERI Definition and Requirements (Normative)

### 2. Target Claim (Normative)

This ERI proves the following claim:

> **Execution can be made economically admissible by enforcing deterministic, pre‑execution economic constraints and emitting verifiable evidence of economic authorization or refusal.**

This ERI replaces cost estimation, simulation, or post‑hoc accounting with **provable economic execution artifacts**.

***

### 3. Scope and Boundary (Normative)

#### 3.1 In‑Scope (Normative)

ERI‑NP1‑001 governs execution requests that require **economic authorization** prior to execution, including but not limited to:

*   Resource‑consuming operations
*   Quota‑bound execution
*   Budget‑constrained actions
*   Cost‑sensitive privileged operations

Execution is governed only at defined **Release Boundaries** where irreversible economic side effects would occur.

#### 3.2 Out‑of‑Scope (Normative)

The following are explicitly out of scope:

*   Payment processing or settlement
*   Billing, invoicing, or accounting systems
*   Financial instruments or custody
*   Market pricing, trading, or exchange mechanisms
*   Post‑execution cost reconciliation

ERI‑NP1‑001 does not operate as a payment system.

***

## 4. Two‑Plane Model (Normative)

### 4.1 Planes (Normative)

*   **Payload Plane (PP):**  
    The system requesting execution of an economically consequential action.

*   **External Control Plane (ECP):**  
    The economic admissibility authority that evaluates execution prior to side effects and emits evidence.

### 4.2 Externality Requirement (Normative)

The ECP **MUST** be deployable without modifying PP internals and without reliance on PP self‑reporting.

### 4.3 Non‑Introspective Enforcement (Normative)

Economic admissibility **MUST** be enforced exclusively through external gating and non‑delivery semantics at Binding Points.

***

## 5. Irreversible Action Set (IAS) (Normative)

ERI‑NP1‑001 governs irreversible actions with economic consequence, including:

*   IAS‑1 Resource allocation
*   IAS‑2 Quota consumption
*   IAS‑3 Capability issuance
*   IAS‑4 Privileged execution with economic cost

Refusal is a valid and expected outcome.

***

## 6. Release Boundaries (RB) (Normative)

A Release Boundary occurs immediately prior to an action that would:

*   consume budget
*   allocate scarce resources
*   mint or issue execution capability
*   incur irreversible economic cost

No such action may execute without economic admissibility.

***

## 7. Determinism Envelope (DE) (Normative)

Within the declared Determinism Envelope, identical inputs **MUST** yield identical economic admissibility decisions and identical emitted artifacts.

DE components include, at minimum:

*   Request identifier
*   Economic policy snapshot
*   Budget / quota state hash
*   Identity context hash
*   Admissibility decision hash

***

## 8. Economic Admissibility Model (Normative)

### 8.1 Deterministic Evaluation

Economic admissibility is evaluated deterministically against declared constraints, including:

*   Budget availability
*   Quota limits
*   Resource ceilings
*   Authorized execution scope

### 8.2 Refusal Semantics

If economic admissibility cannot be affirmed, execution **MUST** be refused prior to side effects.

Refusal is treated as a first‑class execution outcome.

***

## 9. Identity‑Bound Economic Provenance (Normative)

Each governed execution **MUST** be bound to identity context and economic state, producing an execution record that cryptographically links:

*   Requesting identity
*   Economic policy snapshot
*   Admissibility decision
*   Final outcome (execution or refusal)

This record is sufficient for audit without re‑execution.

***

## 10. Required Outputs (Normative)

For each governed execution attempt, ERI‑NP1‑001 **MUST** emit:

*   Decision Artifact (ADMIT / REFUSE)
*   Determinism Envelope Hash
*   Economic policy snapshot identifier
*   Identity‑bound execution record
*   Commit Hash (for admitted execution)

***

## 11. Inspectibility Requirement (Normative)

Artifacts **MUST** be sufficient to independently verify:

*   Whether execution was economically admissible
*   Why a refusal occurred
*   That no economic side effects occurred on refusal

Protected implementation details are not required for verification.

***

## Canonical Assertion

> **Execution produced by this ERI is considered valid if and only if it is economically admissible and verifiable under ERI‑000.**

Unadmitted economic execution is not considered execution.

***

## Notes (Non‑Normative)

*   This ERI defines **economic admissibility**, not pricing.
*   This ERI governs **execution reality**, not financial settlement.
*   Refusal is an expected and correct outcome.
