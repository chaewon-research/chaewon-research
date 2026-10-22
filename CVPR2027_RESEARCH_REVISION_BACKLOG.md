# CVPR 2027 — Research Revision / Addition / Removal Backlog

**Prepared:** 2026-10-21  
**Purpose:** An evidence-backed action register for **revising existing work rather than repeatedly pivoting**.  
**Status:** Planning audit only. No code, models, datasets, manuscripts, or experiment results were changed as part of this audit.  
**Scope:** The existing research theme and four most directly related public repositories: `visual-geometric-solver-generalization` (primary unfinished vision project), `diffusion-missing-curve-experiments` (secondary exploratory vision work), `operator-conditioned-mixed-precision` (accepted WACV 2027 prior work), and `qdc-fractional-neural-operators` (existing numerical-efficiency foundation). This is **not** a line-by-line code review of every repository.

## 0. Non-negotiable scientific gate

The exact overarching theme from the [GitHub profile README](https://github.com/chaewon-research/chaewon-research/blob/main/README.md) is:

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

The user's rule is **direct alignment with this theme**. The following C/I/P/T questions *operationalize* that rule; they are not separate rules attributed to the user:

- **C — Cost:** What actual ML computation, memory, bandwidth, energy, or latency would be reduced?
- **I — Critical internals:** Which identifiable internal model computations or representations are hypothesized to matter for a capability?
- **P — Preservation:** Which capability must remain intact (including how it will be measured)?
- **T — Test:** Which mechanism-specific intervention and cost-matched control would disprove or support the connection?

**Do not recommend a CVPR topic** if any of C/I/P/T is missing. A **conceptually aligned hypothesis** is not an experimentally validated result or a novel paper. **Generalization accuracy alone, without critical-internal-computation and cost-reduction claims, does not satisfy the theme.**

## 1. Decision summary

**Current decision: REVISE, DO NOT PIVOT. But DO NOT declare an existing project CVPR-ready.**

1. The existing geometric-solver project is the **primary unfinished experimental artifact** to audit and stabilize, *not* an already suitable CVPR contribution. Its newest [replication-first plan](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/replication_first_plan.md) correctly prioritizes reproduction of the authors' released checkpoint/data/evaluator before custom training.
2. A standalone held-out-H geometric generalization study currently **fails the above CVPR theme gate** unless it is explicitly coupled to an experiment on reducing computation while preserving a critical internal operation/representation and valid geometric-solving ability.
3. The accepted [WACV 2027 paper](https://github.com/chaewon-research/operator-conditioned-mixed-precision) is **prior accepted work, not a manuscript to revise and resubmit to CVPR**. New work must be materially different.
4. The missing-curve diffusion experiments are exploratory, and the [README](https://github.com/chaewon-research/diffusion-missing-curve-experiments) says missing-region recovery remains weak. Do not promote them into a proven reconstruction/acceleration result.
5. QDC has reproducibility assets and prior selective-precision insights, but applying the same technique to vision without a distinct question is not automatically new.

**Go/no-go status: NO SUBMISSION-SUPPORTED CVPR 2027 PAPER ESTABLISHED** as of this audit. The fastest defensible route is to repair baseline/evaluation first and run one decisive compute-preservation pilot *only after* a working baseline exists. No new topic is selected here.

**Priority legend:** P0 = scientific or submission blocker; P1 = required for a serious new paper after P0; P2 = later quality improvement.  
**Action legend:** REVISE = correct an existing protocol/claim/document; ADD = new evidence/artifact; REMOVE/DEFER = stop an unsupported claim, analysis, or activity (never delete negative data).

## 2. P0 — Immediate blockers (revise / add / remove)

| ID | Action | Exact change | Evidence / location | Completion test |
| --- | --- | --- | --- | --- |
| P0-01 | **REVISE** | Adopt one source-of-truth baseline: authors' original released curve checkpoint, dataset, and **pinned** scoring implementation; do not mix original-data vs held-out-H data or original vs custom scores. | [Replication-first plan](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/replication_first_plan.md); [original CVPR 2026 paper](https://openaccess.thecvf.com/content/CVPR2026/html/Goren_Visual_Diffusion_Models_are_Geometric_Solvers_CVPR_2026_paper.html) | Reproduction table says exactly which checkpoint, dataset revision, sampler, seeds, metric implementation, snapping mode, and sample count were used. |
| P0-02 | **ADD** | Execute the already-prepared [original Table 1 Colab](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/notebooks/reproduce_authors_square_table1_colab.ipynb): small smoke test, then a declared representative evaluation with released data, original scorer, before/after snapping and ground-truth continuous metrics. **Do not claim it has been run unless logs/results exist.** | [Original Table 1 replication plan](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/replication_first_plan.md) | Saved manifest, run logs, model/data hashes, Q and alignment means with uncertainty and sample counts; explicit differences vs published Table 1. |
| P0-03 | **REVISE** | Reconcile paper-versus-code methodological conflicts (paper appendix vs release: nominal training budget/batch/epochs and beta/noise schedule). Use the pinned checkpoint/config as operational reference, record every discrepancy; **do not silently hybridize**. | [Paper/code audit](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/replication_first_plan.md) | One provenance table with exact upstream revision, code path, configuration, published description, and decision. |
| P0-04 | **REVISE** | Clearly separate the study's binary criterion (squareness ≥0.85, each corner ≤3 px) from the original paper's continuous Q and negative mean-corner-distance metrics, and separate snapped vs raw predictions. | [Evaluation protocol](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/evaluation.md) | Paper-comparable results never substitute binary passes for Table 1 Q/alignment; every result labels raw/snapped. |
| P0-05 | **ADD** | Audit raster-metric validity and uncertainty: 969/1,000 known-valid constructed masks passed the project binary evaluator. Quantify why the other 31 fail (rasterization/extraction vs geometry); test threshold sensitivity and use geometry-coordinate controls where available. | [Evaluation protocol](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/evaluation.md) | Error-case gallery, false-negative analysis, threshold curve, and a frozen evaluation rule before any new final experiment. |
| P0-06 | **REMOVE/DEFER** | **Do not start another arbitrary five-curve training/loss/LR sweep yet** or silently relabel the small-budget controls as reproduction of published full-data training. Preserve all past checkpoints and negative results. | [Current README](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/README.md) records 0/20 at epochs 30/40, 0/10 five-curve outcomes, balanced-loss/cosine failures and the existing pause decision. | Next experiment is tied to baseline reproduction and a predeclared hypothesis, not another unmotivated tuning iteration. |
| P0-07 | **REVISE** | Correct conclusion scope: the authors' checkpoint achieved **7/20** passes on a small custom study sample, but this is **not** reproduction of published Table 1 nor evidence of held-out-H generalization; its training H distribution covers study groups. | [Pretrained-checkpoint control](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/pretrained_checkpoint_control.md) | Every summary identifies the 20-curve study control as such and avoids direct unmatched comparisons with the custom model's 0/20 at different steps/seeds. |
| P0-08 | **REMOVE/DEFER** | Do **not** package "generalize diffusion on unseen curve H" as the CVPR theme-matching paper by itself. It investigates out-of-distribution solving, not necessarily selective preservation of critical internals under reduced computation. | [Research theme](https://github.com/chaewon-research/chaewon-research/blob/main/README.md); [dataset protocol](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/author_generator_dataset.md) | Any candidate paper begins with explicit C/I/P/T and a falsifiable computation-capability tradeoff. |
| P0-09 | **REMOVE/DEFER** | Do **not** convert the accepted WACV 2027 manuscript into a superficially renamed CVPR 2027 submission. Prepare a novelty/overlap statement before reusing any framework, numerical claims or results. | [WACV accepted paper README](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/README.md); [CVPR 2027 author guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines) | Clear side-by-side comparison of problem, method, claims, experiments and reused figures/tables; no substantially similar submission. |
| P0-10 | **ADD** | Confirm all intended authors' OpenReview profiles and conflicts, author roster and order before paper enrollment; prepare required LLM Usage Statement, double-blind compliant submission, and self-contained materials. | [CVPR 2027 author guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines) | Administration checklist passes before **Nov 10** enrollment; 8-page paper formatting and LLM declaration pass before **Nov 16** full submission. |
| P0-11 | **ADD** | Create a one-page **scientific decision record** for any candidate: hypothesis (C/I/P/T), closest competing publications, current reproducible baseline, distinguishing ablation, fixed compute budget, acceptance/stop criterion, and exact difference from WACV. | This backlog; [SenCache](https://openaccess.thecvf.com/content/CVPR2026/html/Haghighi_SenCache_Accelerating_Diffusion_Model_Inference_via_Sensitivity-Aware_Caching_CVPR_2026_paper.html); [SeaCache](https://openaccess.thecvf.com/content/CVPR2026/html/Chung_SeaCache_Spectral-Evolution-Aware_Cache_for_Accelerating_Diffusion_Models_CVPR_2026_paper.html); [SVD-Cache](https://openaccess.thecvf.com/content/CVPR2026/html/Chen_Forecast_the_Principal_Stabilize_the_Residual_Subspace-Aware_Feature_Caching_for_CVPR_2026_paper.html) | A reviewer could state exactly what new claim would be falsified by a negative result. |

## 3. P1 — Scientific additions **only after** P0 baseline passes

These are *conditional*, not a hidden instruction to pivot or a claim that the proposed method works.

| ID | Action | Required work | Successful evidence / stop condition |
| --- | --- | --- | --- |
| P1-01 | **ADD** | On a validated frozen solver, intervene on **specific internal computations** (e.g., denoiser blocks or selected feature updates), not just overall image quality. Compare full compute, uniform removal, random removal, and an identified critical-computation-preserving policy. | Same test curves/seeds and actual matched GPU latency. If importance cannot be predicted or criticality does not alter capability tradeoffs, stop. |
| P1-02 | **ADD** | State which exact model capability is preserved: valid square constraints, minimum nondegenerate side length, alignment and solution success with uncertainty; avoid labeling output-mask similarity alone as problem-solving. | Report attempt-level and per-instance best-of-k success (not interchangeable), raw and snapped results, continuous Q/alignment, and failure taxonomy. |
| P1-03 | **ADD** | Cost-model audit: report denoiser evaluations, estimated FLOPs *and* synchronized wall-clock GPU latency, memory if relevant, controller overhead, warmup, batch size, hardware and trial distribution. | Actual compute or memory reduction verified under matched inference conditions; speedup is not inferred solely from fewer sampling steps. |
| P1-04 | **ADD** | Strongly competitive prior-art comparisons if the method is diffusion sampling/caching: SenCache, SeaCache, SVD-Cache, DPCache/TAP where architecturally applicable. Explain inapplicability explicitly rather than pretending every published method runs unmodified. | Cost-matched quality/capability–latency frontier and at least one competent published or faithfully implemented baseline. |
| P1-05 | **ADD** | Distinguish "internal representation preserved" from "output still passes." Use feature interventions, targeted ablations, activation/representation diagnostics, and controls that rule out mere extra compute allocation. | Mechanism-specific evidence; otherwise narrow claim to *computation selection* and do not assert representation preservation. |
| P1-06 | **ADD** | Generalization tests only after proven training/replication: non-overlapping seen-group vs held-out H cohorts, held-out generator parameters, multiple independent seeds; no tuning on held-out groups. | Held-out curves evaluated once under frozen policy; results report confidence intervals and paired seed comparisons. |
| P1-07 | **ADD** | A second supported visual task or model (e.g., another geometric task **only if** its released baseline is replicable) to test whether critical-computation findings extend beyond one toy setup. | Same C/I/P/T mechanism across tasks; if second baseline is unavailable, present a narrowly scoped study without claiming generality. |
| P1-08 | **REVISE** | Separate primary scientific claim from auxiliary observations. Main text: one key causal result + method + controlled tradeoff; appendix: training-debugging history, extra threshold plots and optional results. | Each central claim maps to a table/figure with a reproducible script and experimental configuration. |
| P1-09 | **ADD** | Report at least 3 independent runs where feasible; paired uncertainty (bootstrap across curves or properly designed repeated trials), failure stratification, per-H performance and exact sample counts. | No claim depends solely on two favorable seeds or a single cherry-picked example. |
| P1-10 | **REVISE** | Reuse the WACV principle only with an explicit *different* scientific insight; do not assume operator-conditioned dynamic precision, layer skipping, or "which stages matter" is novel. | Novelty table compares WACV question, controller, costs, test domain, and contributions; no duplication or unearned performance transfer. |

## 4. P2 — Secondary and archival work

| ID | Action | Work |
| --- | --- | --- |
| P2-01 | **REVISE** | In [diffusion-missing-curve-experiments](https://github.com/chaewon-research/diffusion-missing-curve-experiments), keep failure to reconstruct withheld segments as the main limitation; do not interpret full-data positive controls as missing-region recovery. Future work needs meaningful reconstruction conditions, matched sampler compute and capability-level metrics before it can become a theme-aligned efficiency project. |
| P2-02 | **ADD** | For the above curve experiments, if resumed later, add matched DDPM/DDIM budgets, uncertainty over more seeds/missing intervals, and tests beyond point occupancy; **do not prioritize ahead of the baseline blocker**. |
| P2-03 | **REVISE** | Treat [QDC](https://github.com/chaewon-research/qdc-fractional-neural-operators) as published/preprint prior foundation for selective numerical correction, not automatically a CVPR proposal. Any transfer must introduce an independently testable CV problem and compare fixed computation budgets. |
| P2-04 | **REVISE** | Treat the [accepted WACV 2027 project](https://github.com/chaewon-research/operator-conditioned-mixed-precision) as a cited, completed baseline. Its 1.44× hardware timing and reconstruction quality were evaluated under **different precision protocols**, so do not merge those into a single matched accuracy-speed claim. |
| P2-05 | **ADD** | Where permissions and licensing permit, make artifact manifests, deterministic seed lists, model hashes, environment and evaluation commands easy to locate. Preserve existing raw failures, logs and checkpoints. |
| P2-06 | **REMOVE/DEFER** | Remove *claims*, not evidence: no "SOTA," "first," "generalizes," "preserves critical representations," or "speedup" without supported comparisons, verified costs and uncertainty. Do not delete negative results or silently alter scoring thresholds. |

## 5. Research/source comparison matrix (as of 2026-10-21)

This is a targeted set of primary sources, **not an exhaustive novelty clearance**:

| Primary source | Implication for revision |
| --- | --- |
| [Goren et al., Visual Diffusion Models are Geometric Solvers, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Goren_Visual_Diffusion_Models_are_Geometric_Solvers_CVPR_2026_paper.html) | Must reproduce their original baseline; geometric solving itself is prior work and not a new contribution. |
| [SenCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Haghighi_SenCache_Accelerating_Diffusion_Model_Inference_via_Sensitivity-Aware_Caching_CVPR_2026_paper.html) | Sample-specific sensitivity-aware caching is established. |
| [SeaCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chung_SeaCache_Spectral-Evolution-Aware_Cache_for_Accelerating_Diffusion_Models_CVPR_2026_paper.html) | Spectral/content structure-aware caching is established. |
| [SVD-Cache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chen_Forecast_the_Principal_Stabilize_the_Residual_Subspace-Aware_Feature_Caching_for_CVPR_2026_paper.html) | Representation subspaces in caching are established; cannot claim "subspace-aware caching" as novelty. |
| [DPCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Cui_Denoising_as_Path_Planning_Training-Free_Acceleration_of_Diffusion_Models_with_CVPR_2026_paper.html) | Global denoising scheduling is established. |
| [TAP, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Zhu_TAP_A_Token-Adaptive_Predictor_Framework_for_Training-Free_Diffusion_Acceleration_CVPR_2026_paper.html) | Probe-driven, token-adaptive denoising predictors are established. |
| [Dual Ascent Diffusion for Inverse Problems, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Kim_Dual_Ascent_Diffusion_for_Inverse_Problems_CVPR_2026_paper.html) | Fast inverse diffusion and measurement faithfulness have strong competing methods. |
| [CVPR 2027 Author Guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines) | Respect 8-page main paper limit, mandatory LLM Usage Statement, prior publication/overlap rules, anonymity, OpenReview, and review responsibilities. |
| [CVPR 2027 Call for Papers](https://cvpr.thecvf.com/Conferences/2027/CallForPapers) | Enrollment Nov 10, paper Nov 16, supplementary Nov 23 — all 2026, AoE. |

## 6. Suggested execution order (not a promise of automatic work)

- **Oct 21–23:** P0-01, P0-03, P0-04, P0-07, P0-09; prepare original evaluator and asset provenance. Complete conference profile/author review in parallel.
- **Oct 23–26:** P0-02 original-baseline replication; P0-05 evaluator audit. Do not start custom training sweeps. If baseline reproduction fails, diagnose this instead of creating a new method.
- **Oct 26–28:** P0-08, P0-11 theme/novelty gate; if baseline is valid and the new question is clearly distinct, run the smallest P1-01 compute-preservation intervention, paired to P1-02/03 measurement.
- **By Oct 28:** **Go/no-go**. Continue as CVPR only if there is (i) a working baseline, (ii) a testable C/I/P/T contribution materially different from WACV and earlier caching work, and (iii) initial evidence of an improved capability–cost tradeoff. Otherwise keep revising for a later venue without pivoting applications under time pressure.
- **Nov 10 / 16 / 23:** Enrollment / manuscript / supplement only if all relevant scientific and administrative blockers are addressed.

## 7. What is explicitly NOT authorized by this backlog

- No deletion of failed experiments, published/accepted work, checkpoints or scientific history.
- No claim that the authors' published Table 1 has already been reproduced.
- No claim that held-out-H generalization has been established.
- No assumption that a partially specified compression or caching idea is CVPR-novel.
- No unrequested pivot to VLM/video/segmentation, and no new training run without a scientifically justified and documented baseline.
- No claim that this review exhaustively audits every GitHub repository, line of code, or relevant paper.

**Final state to track:** baseline reproduction — **pending**; topology/geometry measurement audit — **pending**; distinct compute-preservation mechanism — **unvalidated**; new CVPR 2027 submission readiness — **not established**.
