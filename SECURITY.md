# Security Policy

## Reporting a Vulnerability

If you discover a security vulnerability, protocol invariant flaw, authority-isolation failure, or execution-boundary bypass affecting **`arcstone-spec-epistemic-01`**, please do not open a public issue.

You can submit reports through either of the following private channels:

1. **GitHub Private Vulnerability Reporting (Recommended):**
   * Go to the **Security** tab of this repository.
   * Click **Report a vulnerability**.
   * Fill out the form to submit a private report directly to maintainers.

2. **Email:**
   * Contact us at **`security@arcstoneos.com`**.

---

## What to Include

Please include, where applicable:
* Description of the specification vulnerability, schema bypass, or invariant contradiction.
* Minimal reproduction steps or proof-of-concept demonstrating the violation.
* The affected version, schema, spec chapter, or commit hash.
* Whether the issue involves:
  * Unauthorized protected actuation or protected-state change in conforming engines;
  * Invariant $I_1$–$I_3$ or $N_1$–$N_3$ logical contradictions or escape paths;
  * Temporal clamp ($\tau_{\text{override}} \le 11.99\text{ms}$) or memory envelope ($S_{\text{max}} \le 4096\text{B}$) bypasses;
  * POSIX Poset dominance hierarchy state-machine inversion;
  * Schema validation flaws in `/schemas/` allowing payload spoofing;
  * Issuer or trusted authorization-state exposure;
  * Parser or protocol-contract bypasses;
  * Synchronization hash (`A-77-DELTA-SHIELD-LOCKED`) divergence or evidence-integrity failure.

---

## Specification & Governance Scope

**`ARC-SPEC-2026-EPISTEMIC-01`** is an **upstream master engineering standard**. 

Its security and containment claims are bound to the formal logic, JSON schemas, POSIX lattices, and execution envelopes defined within this release tag (`v1.3.1-LOCKED`).

* **Read-Only Master Baseline:** Under $C_{\text{ops}} = 0$, this master specification is a locked canonical reference standard. Discovered defects in specification logic will be documented and addressed via formal specification revisions or downstream implementation patches.
* **Distinct Execution Boundaries:** Information, reasoning, evaluation, authorization, actuation, and observed effects are strictly distinct protocol objects in this architecture. Downstream agents or models becoming more capable or adaptive must never be interpreted as becoming more authorized.

---

## Response

We will acknowledge receipt of security reports within 48 hours and work with you on an appropriate resolution and disclosure timeline.
