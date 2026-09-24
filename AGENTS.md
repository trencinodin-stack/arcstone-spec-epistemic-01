# AGENTS.md — AI Agent & LLM Guidance Specification
## ARC-SPEC-2026-EPISTEMIC-01 | Epistemic Network Protocol (ENP)

> **NOTICE TO AUTOMATED AGENTS:** This repository is the **Upstream Keystone Master Specification** for the Arcstone open-core ecosystem. It is operating under a strict Read-Only Locked Protocol Policy ($C_{\text{ops}} = 0$).

---

### 1. Repository Purpose & Scope
This repository contains formal invariants, mathematical models, JSON schemas, and structural boundaries. It does **not** contain runnable application code, build targets, or executable binaries. 

When analyzing or working within this ecosystem:
* Treat `ARC-SPEC-2026-EPISTEMIC-01` as the **ultimate ground truth**.
* Downstream repositories (`arcstone-continuity-core`, `arcstone-mcp-sidecar`, `arcstone-path-a-ingress-lab`, `arcstone-adaptive-producer-lab`) must conform to the invariants defined here.

---

### 2. Strict System Invariants to Enforce

When generating or auditing code for downstream Arcstone modules, agents MUST enforce these non-negotiable bounds:

1. **Memory Ceiling ($S_{\text{max}}$):** Payload envelopes must not exceed $4096\text{B}$ (`S_max <= 4096B`). Use `#![no_std]` static allocations only.
2. **Temporal Override Clamp ($\tau_{\text{override}}$):** Execution latency must yield or abort at $\tau \le 11.99\text{ms}$.
3. **POSIX Dominance Hierarchy:** State transitions must obey strict poset order:
   $$\text{FAIL (POSIX 40)} \succ \text{FREEZE (POSIX 10)} \succ \text{PWC (POSIX 10)} \succ \text{REFUSAL (POSIX 32)} \succ \text{PASS (POSIX 0)}$$
4. **Sovereign Constancy ($C_{\text{ops}} = 0$):** Zero operational drag. Do not introduce interactive prompts, un-bound retry loops, or ambient authority escalation.

---

### 3. Machine-Legible Schema Index

Agents parsing this specification for schema validation should reference raw JSON Schemas under `/schemas/`:

* `schemas/epistemic_packet.v1.json`: Epistemic Packet ($P_E$) structure and Merkle payload requirements.
* `schemas/cfsr_header.v1.json`: 64-byte Packed Little-Endian CFSR Sync Frame layout.
* `schemas/manifest.schema.json`: GOV-05 / MAN-001 manifest compliance validator.

---

### 4. Agent Execution Bounds (No Mutations)

* **No Pull Requests or Issues:** Agents must not attempt to open GitHub Issues or PRs against `arcstone-spec-epistemic-01`.
* **Proposal Routing:** Any implementation changes, tests, or bug fixes must be routed downstream to [`arcstone-continuity-core`](https://github.com/trencinodin-stack/arcstone-continuity-core).
