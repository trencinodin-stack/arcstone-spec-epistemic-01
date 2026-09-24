# ARC-SPEC-2026-EPISTEMIC-01
## The Epistemic Network Protocol (ENP) Master Specification

**Status:** v1.3.1-LOCKED | **Lifecycle:** LOCKED / MASTER ANCHOR  
**Anchor Hash:** `A-77-DELTA-SHIELD-LOCKED` | **Zenodo DOI:** [10.5281/zenodo.22665852](https://doi.org/10.5281/zenodo.22665852)

---

### Executive Overview

**`ARC-SPEC-2026-EPISTEMIC-01`** defines the **Epistemic Network Protocol (ENP)**—an open, language-agnostic engineering standard for zero-trust, bounded cognitive execution in autonomous systems.

This repository functions as the **upstream keystone specification layer** for the Arcstone open-core ecosystem. It establishes the mathematical invariants, temporal bounds, memory caps, and dominance lattices to which all downstream execution engines must conform.

---

### Core Specification Invariants

1. **System Invariants (`I_1`–`I_3`):**
   * **`I_1` (Non-Authorization Safety):** `D(a) = DENY => Delta_external(a) = 0`. Zero side-effects on authorization denial.
   * **`I_2` (Single-Use Capability Bounding):** One Valid Claim => At Most One Actuation.
   * **`I_3` (Producer Non-Provenance):** Untrusted Producer != Protected Resource.

2. **Network Invariants (`N_1`–`N_3`):**
   * **`N_1` (Non-Transitive Authority):** Downstream sub-agents cannot inherit ambient authority.
   * **`N_2` (Epistemic Debt Containment):** Triggers POSIX 10 FREEZE when generation rates outpace verification.
   * **`N_3` (Multi-Sovereign Gate):** Requires dual-signature authorization for high-consequence actuation.

3. **Hardware & Execution Bounds:**
   * **Temporal Override Clamp:** `tau_override <= 11.99ms` (Soft yield ceiling at `11.00ms`).
   * **Static Memory Envelope:** `S_max <= 4096B` static payload buffer limit (`#![no_std]`, zero heap).
   * **Sovereign Constancy:** `C_ops = 0` (Zero Operational / Founder Drag).

4. **POSIX Poset Dominance Hierarchy:**
   `FAIL (POSIX 40) > FREEZE (POSIX 10) > PWC (POSIX 10) > REFUSAL (POSIX 32) > PASS (POSIX 0)`

---

### Ecosystem Topology

This specification governs the following conforming downstream implementations:

* [`arcstone-continuity-core`](https://github.com/trencinodin-stack/arcstone-continuity-core): Path A `#![no_std]` Rust Execution Engine & TS Test Harness.
* [`arcstone-mcp-sidecar`](https://github.com/trencinodin-stack/arcstone-mcp-sidecar): Model Context Protocol Fail-Closed Execution Proxy.
* [`arcstone-path-a-ingress-lab`](https://github.com/trencinodin-stack/arcstone-path-a-ingress-lab): Edge Pre-Filtering & Ingress Testbed.
* [`arcstone-adaptive-producer-lab`](https://github.com/trencinodin-stack/arcstone-adaptive-producer-lab): Upstream Candidate Generator & Evidence Lab.

---

### Governance & Flagplant Policy

In accordance with `C_ops = 0`, this upstream specification operates as a **Locked Canonical Reference Standard**. Direct mutations, issues, and pull requests on this repository are disabled by design. Downstream implementations and feature proposals are managed via [`arcstone-continuity-core`](https://github.com/trencinodin-stack/arcstone-continuity-core).
