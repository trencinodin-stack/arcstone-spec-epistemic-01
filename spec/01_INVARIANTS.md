# Spec Chapter 01: System & Network Invariants
## Protocol Standard: ENP-SPEC-01-INV

---

### 1. System Invariants (I_1 – I_3)

* **`I_1` (Non-Authorization Safety):**
  $$D(a) = \text{DENY} \implies \Delta_{\text{external}}(a) = 0$$
  Any actuation request $a$ yielding a decision $D(a) = \text{DENY}$ must result in zero external side-effects or state mutations.

* **`I_2` (Single-Use Capability Bounding):**
  $$\text{One Valid Claim} \implies \text{At Most One Actuation}$$
  Capabilities are single-use tokens; reuse triggers immediate consumption invalidation.

* **`I_3` (Producer Non-Provenance):**
  $$\text{Untrusted Producer} \centernot\implies \text{Protected Resource}$$
  Producers cannot assert ambient or structural privilege over downstream protected resources.

---

### 2. Network Invariants (N_1 – N_3)

* **`N_1` (Non-Transitive Authority):** Downstream sub-agents cannot inherit ambient authority across delegation boundaries.
* **`N_2` (Epistemic Debt Containment):** If candidate proposal generation rate exceeds verification capacity ($\dot{G} > \dot{V}$), the system forces a POSIX 10 `FREEZE`.
* **`N_3` (Multi-Sovereign Gate):** High-consequence actuation boundaries require dual-signature sovereign authorization.
