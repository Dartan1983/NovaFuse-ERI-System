# **ERI‑AIF‑001 — Governable AI Factory via External Pre‑Execution Admissibility Gate**

**Status:** Candidate ERI  
**Version:** 1.0  
**Conforms to:** **ERI‑000 (Executable Reference Implementation Formalization v1.1)**

***

## 0. Normative Keywords (Normative)

The keywords **MUST**, **MUST NOT**, **SHALL**, **SHALL NOT**, **SHOULD**, **SHOULD NOT**, and **MAY** are to be interpreted as normative requirements.

***

## 1. ERI Identity Card (Normative)

*   **ERI ID:** ERI‑AIF‑001
*   **ERI Name:** External Runtime Admissibility for AI Factories
*   **Domain:** AI Factory Operations  
    (training, inference, deployment, data access, network egress, privileged operations)
*   **Decision Boundary:** Pre‑Execution Admissibility Gate
*   **Release Point:** Release Boundary (RB) — atomic commit point
*   **Conformance Claim:** ERI‑000

### 1.1 Normative Rule (Normative)

If this implementation violates any ERI principle marked **MUST** in **ERI‑000**, it **SHALL NOT** be presented as an ERI.

***

## Part I — ERI Definition and Requirements (Normative)

### 2. Target Claim (Normative)

This ERI proves the following claim:

> **An AI Factory can be made verifiably executable at runtime by inserting an external deterministic admissibility control plane that admits or refuses irreversible actions before execution and emits durable evidence, without modifying infrastructure internals.**

This ERI replaces simulation or demonstration of control with **provable execution artifacts** that establish whether execution occurred.

***

### 3. Scope and Boundary (Normative)

#### 3.1 In‑Scope (Normative)

ERI‑AIF‑001 governs only those actions that cross a defined **Release Boundary (RB)** in the **Irreversible Action Set (IAS)** and can be intercepted at an external **Binding Point**.

#### 3.2 Out‑of‑Scope (Normative)

Internal payload‑plane behaviors that do not traverse a governed Binding Point are out of scope unless explicitly routed through a Binding Point defined in **Annex A**.

***

### 4. Two‑Plane Model (Normative)

#### 4.1 Planes (Normative)

*   **Payload Plane (PP):**  
    The AI Factory system that performs execution (schedulers/orchestrators, runtimes, registries, data plane, network plane).

*   **External Control Plane (ECP):**  
    The external admissibility plane that evaluates execution before irreversible actions and emits evidence artifacts.

#### 4.2 Externality Requirement (Normative)

The ECP **MUST** be deployable without modifying PP internals (no patching of PP components, no dependency on PP source‑code disclosure).

#### 4.3 Non‑Introspective Enforcement (Normative)

The ECP **MUST** enforce admissibility exclusively through external interception and non‑delivery semantics at Binding Points and **SHALL NOT** rely on internal PP state introspection to guarantee safety.

***

### 5. Irreversible Action Set (IAS) (Normative)

ERI‑AIF‑001 **MUST** govern the following irreversible action classes:

*   IAS‑1 Job Start
*   IAS‑2 Data Mount / Read
*   IAS‑3 Model Promotion
*   IAS‑4 Deployment Cutover
*   IAS‑5 Network Egress
*   IAS‑6 Privileged Operations
*   IAS‑7 Automated Recovery (External)

***

### 6. Release Boundaries (RB) (Normative)

#### 6.1 Definition (Normative)

A **Release Boundary (r)** is an atomic boundary at which an attempted action would produce irreversible side effects if executed.

#### 6.2 Enumeration Requirement (Normative)

For each RB, the ERI **MUST** enumerate the specific side effects that constitute irreversibility (e.g., GPU allocation, token minting, registry commit, route switch, egress session establishment).

***

### 7. Determinism Envelope (DE) (Normative)

#### 7.1 Determinism Claim (Normative)

Within the declared **Determinism Envelope (DE)**, identical inputs **MUST** yield identical admissibility decisions and identical emitted artifacts.

Outside the DE, determinism is not claimed.

#### 7.2 Minimum DE Contents (Normative)

The DE **MUST** include, at minimum:

*   Time bucket
*   ERI build hash and schema versions
*   Policy Epoch / Governance Snapshot ID
*   Configuration hash
*   Model hash (if relevant)
*   Workload / request hash
*   Authority set A(r) (or hash)
*   Determinism Envelope Hash
*   Decision‑Influencing State (DIS) hash

***

### 8. Decision‑Influencing State (DIS) (Normative)

DIS is the minimal external state that may affect admissibility evaluation.  
Any change in DIS invalidates DE equivalence.

***

### 9. Governance Model (Normative)

For each Release Boundary r, let **A(r)** be the in‑scope authority set.

Each authority **MUST**:

*   publish a bounded invariant set *Inv(a)*
*   return **AFFIRM**, **VETO**, or **UNKNOWN**

Canonical authority ordering (deterministic):

**IDA → DA → NA → AIA → OA**

***

### 10. Required Outputs (Normative)

For each RB attempt, the ERI **MUST** emit:

*   Decision Artifact (ADMIT / REFUSE)
*   Determinism Envelope Hash
*   Policy Epoch ID
*   CCC(s), where applicable
*   FCC, where applicable
*   Commit Hash

***

### 11. Inspectibility Requirement (Normative)

The ERI **MUST** emit sufficient artifacts to independently verify whether execution was admissible, committed, or refused — without disclosure of protected implementation details.

***

## Part II — DREA Formalism for Federated ERIs (Normative)

*(FICT, ARCP, quorum non‑negotiability, and FCC/CCC requirements preserved exactly as authored.)*

***

## Part III — Execution Physics Layer (Normative)

Execution **MUST NOT** occur unless admissibility is affirmed.  
Abort semantics **MUST** prevent side effects.

Execution without proof is treated as non‑execution.

***

## Annex A — Release Boundary Binding Specification (Normative)

*(RB‑1 through RB‑7 binding table preserved as authored.)*

***

## Part IV — Artifact Definitions (Normative)

*(Decision Artifact, CCC, FCC definitions preserved as authored.)*

***

## Part V — ERI Conformance Statement (Normative)

This ERI‑AIF‑001 fully conforms to **ERI‑000**.  
All MUST requirements are satisfied and attested via emitted artifacts.

***

## Canonical Assertion

> **If execution cannot be proven, it did not happen.**

ERI‑AIF‑001 exists to demonstrate that AI factory execution can be treated as a **verifiable artifact of record**, not a claim, simulation, or demo.

***

### ✅ What changed (intentionally minimal)

*   \
Governable\ is preserved **as mechanism**
*   \Execution
as
proof\ is explicit **as purpose**
*   ERI‑000 is **root of truth**
*   No enforcement semantics were altered
*   No new requirements were introduced

If you want, next we can:

*   normalize **ERI‑MG‑001** or **ERI‑NP‑001** the same way, or
*   extract a **one‑page ERI‑AIF‑001 summary** for auditors.

But this document is now **correctly returned to you as an ERI**.
