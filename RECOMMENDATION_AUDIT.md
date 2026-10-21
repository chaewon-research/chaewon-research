# Audit of Previous CVPR Research Recommendations

**Audit date:** 2026-10-21  
**Scope:** Recommendations made in the conversation before this audit. No new experiments were run.  
**Status:** **No previously recommended idea is currently certified as both theme-aligned and CVPR-ready.** Conceptual eligibility is not publication readiness.

## Standard applied

The user's single hard rule is **direct alignment with the exact research theme** in [README.md](README.md):

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

For each idea: state the intended computational reduction, the internal computation or representation claimed to be critical, the model capability to preserve, and a discriminating experiment. These four questions operationalize the user's rule; they are *not* an independent replacement for the rule. An explicit, testable *hypothesis* can pass theme alignment without having results. No recommendation should be presented as the **best practical CVPR choice** without separate novelty, evidence, and feasibility checks.

## Retrospective decision log

### A. Dual-Budget Diffusion (initial recommendation)

- **Compute:** avoid costly denoiser evaluations using an approximate path.
- **Critical internals:** not originally pinned to a concrete internal feature, unit, or computation; measurement-visible and null-space error were described, but the mechanism of essential computation was largely assumed.
- **Preserved capability:** inverse reconstruction fidelity and agreement with measurements.
- **Test:** compare cost-matched denoising policies and separately measure approximation damage to observable/weakly observed components.
- **Theme judgment:** **INSUFFICIENTLY SPECIFIED AS RECOMMENDED**. A tighter intervention on identified internal computations could make a *new version* eligible. Do not retrofit this missing claim and call the original compliant.
- **CVPR judgment:** **DO NOT RECOMMEND AS IS**. Prior-art overlap, difficult error estimation, and no demonstration of compute savings.

### B. Operator-Conditioned Critical Computation / Stage Skipping

- **Compute:** omit or approximate specific reconstruction-model stages.
- **Critical internals:** stage-specific computations whose impact on capability may change across sensing operators.
- **Preserved capability:** reconstructed-image fidelity under a fixed compute budget.
- **Test:** counterfactually disable stages across operators, compare stage rankings, evaluate on held-out operators and at matched measured runtime.
- **Theme judgment:** **CONCEPTUAL PASS**, because the hypothesis directly couples internal computation importance, computational reduction, and capability preservation. **NOT EMPIRICALLY VALIDATED.**
- **CVPR judgment:** **NOT RECOMMENDED YET**. Major distinction from already accepted operator-conditioned mixed precision work is unresolved; feasibility of stage skipping and runtime gains has not been shown.
- **Existing evidence:** [WACV 2027 accepted operator-conditioned mixed-precision project](https://github.com/chaewon-research/operator-conditioned-mixed-precision). This supports domain experience but *does not demonstrate stage-skipping benefits.*

### C. Capability-Critical Computation in Visual Geometric Solvers

- **Compute:** remove selected denoiser evaluations.
- **Critical internals:** denoising steps (a specific class of internal computations); a deeper feature/representation-level explanation remains unproven.
- **Preserved capability:** generation of geometrically valid inscribed squares.
- **Test:** leave-one-step-out or budgeted schedule interventions, compare validity at matched GPU latency, repeat on independent curves and a second task.
- **Theme judgment:** **CONCEPTUAL PASS IN ITS EXPLICIT COUNTERFACTUAL FORM**, not merely because it uses diffusion or geometry. **NOT EMPIRICALLY VALIDATED.** The original recommendation overstated strength and readiness.
- **CVPR judgment:** **DO NOT PRIORITIZE** under the current experimental evidence. The custom model has not demonstrated reliable multi-curve generation; without a credible full-compute baseline, claimed preservation under skipped compute is ill-posed.
- **Negative results (must not omit):** [geometric-solver experiment README](https://github.com/chaewon-research/visual-geometric-solver-generalization) reports 0/20 passes for matched epochs 30 and 40, 0/10 five-curve training outputs, and a separately pretrained control with 7/20 passes; it explicitly advises pausing new training variants pending collaborator discussion. These are **different protocols**, not a controlled head-to-head comparison.

### D. Generic visual-token pruning / generic adaptive diffusion acceleration

- **Compute:** fewer tokens or denoiser steps.
- **Critical internals:** unspecified beyond "important tokens" or "redundant steps".
- **Preserved capability:** often asserted vaguely or replaced by broad output-quality metrics.
- **Test:** mechanism-specific interventions, distinct from generic confidence-based pruning, were not supplied.
- **Theme judgment:** **FAIL AS A BARE TOPIC**, pending a clearly specified scientific claim. Prior work also makes generic novelty claims untenable.

## Overall disposition

**None of the previous suggestions is cleared here as a best CVPR 2027 submission idea.** This does *not* mean conceptual research is impossible: B and C satisfy the overarching theme as *proposals*, but lack key evidence/novelty/readiness to support recommending them as the top submission. A and D were too underspecified.

Before recommending a new top candidate, perform a **fresh search across different ML/vision architecture families**, apply the theme gate *before* selecting a convenient repository, document strongest prior papers with sources, review latest negative GitHub results, and fill the [policy's decision record](RESEARCH_RECOMMENDATION_POLICY.md). If none clears the separate evidence/novelty/feasibility checks, say **no viable recommendation yet**.

## Audit's limitations

This is a source-based retrospective correction, **not** an empirical benchmark, an exhaustive prior-art survey, or proof of CVPR acceptance prospects. Repo statements are cited as repo-reported findings, not independently reproduced data.
