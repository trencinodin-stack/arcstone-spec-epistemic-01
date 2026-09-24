# Spec Chapter 03: Graph Stability Index (GSI)
## Protocol Standard: ENP-SPEC-03-GSI

---

### Mathematical Definition

The Graph Stability Index (GSI) measures structural drift across execution topologies:

$$\text{GSI} = 1.0 - \min\left(1.0, \frac{\Vert{}\mathbf{A}_{\text{configured}} - \mathbf{A}_{\text{runtime}}\Vert{}_F}{\Vert{}\mathbf{A}_{\text{configured}}\Vert{}_F + \epsilon}\right)$$

Where:
* $\mathbf{A}_{\text{configured}}$ is the adjacency matrix of the baseline topology.
* $\mathbf{A}_{\text{runtime}}$ is the empirical adjacency matrix during execution.
* $\Vert{}\cdot\Vert{}_F$ represents the Frobenius norm.
* $\epsilon = 10^{-6}$ prevents division by zero.

### Enforcement Clamps

* **$\text{GSI} = 1.0$:** Complete structural alignment. Normal operation (`PASS`).
* **$0.95 \le \text{GSI} < 1.0$:** Minor drift detected. Triggers `PWC` (POSIX 10).
* **$\text{GSI} < 0.95$:** Severe topology distortion. Triggers immediate `FREEZE` / `FAIL` state.
