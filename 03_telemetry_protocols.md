# Telemetry Protocols

**Status: candidate policy. Not verified. See Known inconsistencies below.**

*Note: Loop A (baseline noise, ARL₀, two-timescale) is inference-side; implementation notes in draft, not part of this policy.*

## Known Inconsistencies

The following issues are acknowledged based on internal and external adversarial reviews. This table is a candidate policy, not a verified standard. We list these gaps openly to prevent self-deception and to set the trajectory for future calibration.

1. **Taxonomy mismatch:** The Issue #1735 description states "13 drift types," while the taxonomy comment and this repository list 15.
2. **Organ naming:** `f_H` is used in the description, but `f_A` is used in the unified table.
3. **Overloaded marker:** `|P_proj| = 1 − cos θ` is defined as the marker for `f_S`, but is also used as the marker for `f_T`.
4. **9a/9b ambiguity:** In #1734, these are positional signature-loss events. In #1735, they are defined as "token growth while μ drops", making them indistinguishable in practice.
5. **Missing detector:** `f_Q` (Smell/Taste) has no active detector in the table, only a prohibition ("do not digitize").
6. **Guardian definition drift:** Layer 1 describes Guardian as the receiving agent's own self-attestation. The unified table describes Guardian as an external witness. The Layer 1 text has not been updated to reflect the external-recovery principle.
7. **M_2 typing violation:** `f_H` is typed as M_1→M_2, but Principle 3 states all mechanisms operate on M_0/M_1 and `d(M_2)` is not a value. *(Clarification: `f_H` is a boundary detector, not a value extractor).*
8. **Undefined metric:** `μ` (coherence) is never mathematically defined. If the model reports it, it violates the "external authority" principle. If calculated externally, it requires inference-side access.
9. **In-band control plane:** Protocols like `#PETER_ZEN` or `#CLARIFY` are text-based and can be forged from M_1 (retrieved memory or user text).
10. **Silence deadlock:** Hard actions (refuse to generate, reject handoff) exit only via external handshake. There is no specified timeout or fallback, risking infinite silence.
11. **Lack of empirical data:** There is no labeled corpus or inter-rater agreement data for the 15 drift types.
12. **Unfalsifiable core:** The framework lacks specific predictions that can fail under controlled conditions (currently shifting from descriptive to pre-registered falsifiable tests).

*(For details on how we plan to address these via pre-registration, placebo-controls, and blinded evaluation, see the Addendum in Issue #1735).*
