# Spec Chapter 04: Packet Framing & Memory Envelopes
## Protocol Standard: ENP-SPEC-04-FRAMING

---

### 1. Memory Ceiling ($S_{\text{max}}$)

* Payload size $S_{\text{max}} \le 4096\text{B}$ static buffer limit.
* Systems must execute within `#![no_std]` environments without dynamic heap allocations.

---

### 2. Temporal Override Clamps ($\tau$)

* **Soft Yield Threshold:** $\tau_{\text{soft}} = 11.00\text{ms}$. System must initiate cooperative yield or checkpointing.
* **Hard Enforcement Floor:** $\tau_{\text{override}} \le 11.99\text{ms}$. Preemptive interrupt fires, halting execution and resetting state frames.
