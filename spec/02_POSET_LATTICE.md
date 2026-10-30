# Spec Chapter 02: POSIX Poset Dominance Hierarchy

**Protocol Standard:** ENP-SPEC-02-LATTICE  
**Normative Overlay:** ARC-ERR-2026-001 | **Master Anchor:** `A-77-DELTA-SHIELD-LOCKED`

### Dominance Relation Mechanics

All state transitions in the Epistemic Network Protocol must conform to the 6-tier operational Partially Ordered Set (Poset) dominance hierarchy ($E$):

$$\text{BREACH (POSIX 40)} \succ \text{REFUSAL (POSIX 32)} \succ \text{CORRUPT (POSIX 30)} \succ \text{PWC (POSIX 12)} \succ \text{FREEZE (POSIX 10)} \succ \text{PASS (POSIX 0)}$$

### Return Code Mappings

| Dominance Order | POSIX Code | Status Name | Operational Action |
|:---|:---|:---|:---|
| **1 (Highest)** | `40` | `BREACH` | Hard terminal abort; TCB violation, NMI lockout, `CLFLUSH`, and immediate resource containment. |
| **2** | `32` | `REFUSAL` | Non-fatal policy envelope rejection; queue drop without global latching. |
| **3** | `30` | `CORRUPT` | Schema, CRC, or payload limit fault ($S > 4096\text{ B}$); rejects state write. |
| **4** | `12` | `PWC` | **[Canonical Lock per ARC-ERR-2026-001]** Pending Worker Clearance; holds execution pending explicit out-of-band token verification; page tables read-only. |
| **5** | `10` | `FREEZE` | Runtime scheduling yield ($\tau_{\text{override}} \le 11.99\text{ ms}$); execution pause outside $\operatorname{Im}(\Phi)$ to contain epistemic debt. |
| **6 (Lowest)** | `0` | `PASS` | Execution validated; nominal release; capability token redeemed. |

> **Functorial Bridge Note:** The pre-ingress join-semilattice $L = \{\bot, \ell_1, \ell_2, \ell_3, \top\}$ maps to $E$ via covariant functor $\Phi$, where $\operatorname{Im}(\Phi) = \{0, 12, 30, 32, 40\}$. `POSIX 10 (FREEZE)` operates as an internal runtime scheduling yield outside $\operatorname{Im}(\Phi)$.
