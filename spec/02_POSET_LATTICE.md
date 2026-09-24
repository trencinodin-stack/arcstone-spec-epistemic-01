# Spec Chapter 02: POSIX Poset Dominance Hierarchy
## Protocol Standard: ENP-SPEC-02-LATTICE

---

### Dominance Relation Mechanics

All state transitions in the Epistemic Network Protocol must conform to a strictly ordered Partially Ordered Set (Poset) dominance hierarchy:

$$\text{FAIL (POSIX 40)} \succ \text{FREEZE (POSIX 10)} \succ \text{PWC (POSIX 10)} \succ \text{REFUSAL (POSIX 32)} \succ \text{PASS (POSIX 0)}$$

### Return Code Mappings

| Dominance Order | POSIX Code | Status Name | Operational Action |
| :--- | :--- | :--- | :--- |
| **1 (Highest)** | `40` | `FAIL` | Hard terminal abort; immediate resource containment. |
| **2** | `10` | `FREEZE` | Execution pause; halt processing due to debt capacity breaches. |
| **3** | `10` | `PWC` | Proceed With Caution; elevated monitoring & rate-clamping. |
| **4** | `32` | `REFUSAL` | Non-fatal rejection of unauthorized proposal. |
| **5 (Lowest)** | `0` | `PASS` | Execution validated; capability token redeemed. |
