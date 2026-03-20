# NovaFuse ERI System
![Execution Proof System](https://img.shields.io/badge/System-Execution%20Proof%20System-blue) ![Specification Status](https://img.shields.io/badge/Specification-Formal-black) ![Normative Authority](https://img.shields.io/badge/Authority-Normative-red) ![Conformance Required](https://img.shields.io/badge/Conformance-Mandatory-orange) ![License](https://img.shields.io/badge/License-Apache%202.0%20%2B%20CC--BY--4.0-green)
---
The **NovaFuse ERI System** defines a formal, verifiable, and enforceable framework for transforming execution into a **provable artifact of record**.

An Executable Reference Implementation (ERI) replaces demonstrations, simulations, and claims with **deterministic, replayable, evidence-bound execution artifacts**.  
If an execution cannot be proven, it is not considered real.

---

## License (Split Licensing)

This repository uses **split licensing**:

- **Code, schemas, tooling, and executable artifacts** are licensed under **Apache License 2.0** (SPDX: `Apache-2.0`).
- **Specification text and documentation** (including `ERI-000-Formalization/`, `docs/`, and other Markdown spec content) are licensed under **Creative Commons Attribution 4.0 International** (SPDX: `CC-BY-4.0`).

See:
- `LICENSE` (Apache-2.0)
- `LICENSES/CC-BY-4.0.txt` (CC-BY-4.0) *(if present)*

---

## Core Principle

Execution is not accepted as valid unless it is:

- **Identified** — bound to a verifiable authority and context
- **Governed** — evaluated against explicit admissibility rules
- **Verifiable** — emitting sufficient evidence for independent review
- **Admissible** — affirmed by all required authorities

Unverified execution is not accepted as execution.

---

## System Layers

The NovaFuse ERI System is organized into the following layers, each serving a distinct role in establishing execution as proof:

- **ERI Formalization (ERI-000)**  
  Defines the normative requirements, invariants, determinism envelope, and conformance rules that determine what qualifies as an ERI.

- **Verification Model**  
  Defines the structure of admissibility evidence, refusal semantics, and replayable artifacts.  
  This layer specifies *what must be provable*, not how verification is implemented.

- **Enforcement Layer (NAGS)**  
  Enforces admissibility decisions and ensures that only admissible actions are released.

- **Execution Layer (DREA)**  
  Executes admitted actions and prevents side effects for refused actions.

- **Instantiations (ERIs)**  
  Domain-specific Executable Reference Implementations that demonstrate ERI behavior in practice.

---

## Key Property

> An action executes if and only if all required admissibility conditions are satisfied at the point of execution.

Actions that are refused, indeterminate, or unverifiable MUST NOT produce side effects.

---

## Repository Scope

This repository defines:

- Formal execution models
- Governance invariants
- Verification structures
- Interface-level enforcement architecture
- Executable reference instantiations

This repository does **not** define business logic, model internals, or proprietary enforcement implementations.  
Specific enforcement systems may be proprietary.

---

## Canonical Position

NovaFuse maintains the canonical position that **execution credibility precedes trust**.

The ERI System is an **execution proof system**, not an AI product and not a policy framework.  
Execution mechanisms exist within the system as a means to produce verifiable execution artifacts.

For authoritative definitions and conformance requirements, refer to the **ERI-000 Formalization** documents.

---

## Contact

- GitHub: novafuse.technologies@gmail.com

