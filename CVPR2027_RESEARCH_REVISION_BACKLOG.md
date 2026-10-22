# CVPR 2027 — Research Revision / Addition / Removal Backlog

**Prepared:** 2026-10-21  
**Quantitative update:** 2026-10-21 — verified published/repository numbers plus clearly labeled prospective targets; no fabricated experiments.  
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
| P0-02 | **ADD** | Execute the already-prepared [original Table 1 Colab](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/notebooks/reproduce_authors_square_table1_colab.ipynb): small smoke test, then a declared representative evaluation with released data and the upstream scoring formulas. **The repo's replication plan documents a necessary local compatibility repair to the released evaluator (broken helper import / empty-contour handling); record and hash that patch; do NOT call the evaluator unmodified upstream.** Report before/after snapping and ground-truth continuous metrics. **Do not claim it has been run unless logs/results exist.** | [Original Table 1 replication plan](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/replication_first_plan.md) | Saved manifest, run logs, model/data hashes, Q and alignment means with uncertainty and sample counts; explicit differences vs published Table 1. |
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

**Last quantitative source audit:** 2026-10-21. **Evidence labels used below:** VERIFIED-OWN-REPO, VERIFIED-EXTERNAL, DERIVED (calculation from reported counts), TARGET-ONLY (prospective planning), NOT MEASURED. **No invented measurements or results are included.**

## 7. What is explicitly NOT authorized by this backlog

- No deletion of failed experiments, published/accepted work, checkpoints or scientific history.
- No claim that the authors' published Table 1 has already been reproduced.
- No claim that held-out-H generalization has been established.
- No assumption that a partially specified compression or caching idea is CVPR-novel.
- No unrequested pivot to VLM/video/segmentation, and no new training run without a scientifically justified and documented baseline.
- No claim that this review exhaustively audits every GitHub repository, line of code, or relevant paper.

**Final state to track:** baseline reproduction — **pending**; topology/geometry measurement audit — **pending**; distinct compute-preservation mechanism — **unvalidated**; new CVPR 2027 submission readiness — **not established**.


## 8. Quantitative evidence ledger: what has actually been measured

**No "competitive" numbers below are invented.** Past measurements are copied from the specific public project record or an original research article, and they are **not interchangeable across setups**. The planned numerical targets in sections 9–11 are labeled targets, not findings. Do not adjust or cherry-pick trials to make results look plausible, competitive, or "not suspiciously clean"; report all runs including failures.

### 8.1 Existing project evidence — VERIFIED-OWN-REPO

| Provenance | Task / precise protocol | Actually reported result | Interpretation / limitation |
| --- | --- | --- | --- |
| [Geometric solver README](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/README.md) | Epoch-30 conditional model, 99 DDIM steps, small diagnostic samples | **0/20** passes on 10 training curves / 20 generated masks, **0/20** on 10 held-out-group curves / 20 masks | Not an estimate of full held-out-generalization accuracy; poor free generation even on training examples. |
| Same README | Epochs 30 and 40 compared with 25-step DDIM on matched subsets | **0/20** passing attempts at each checkpoint on the reported training/validation tests; training mean squareness **0.223 → 0.192**, validation **0.166 → 0.168** | A longer run did not establish validity; lower epsilon loss is not task success. |
| Same README | New single-curve network, 1,000 optimizer updates, 50 independent pure-noise draws | **29/50** geometric passes (**58%**) on its *one memorized training curve* | Proof that the pipeline can overfit one example, not evidence of multi-curve capability. |
| Same README | Five-curve model, 5,000 successful optimizer updates and 25-step DDIM | **0/10** training-curve passes; **0/10** separate seen-group validation-curve passes per evaluated checkpoint | Model output collapse; 25→99-step sampler comparison also failed to yield foreground at the audited checkpoint. |
| Same README | Five-curve foreground-balanced loss, 5,000 optimizer updates | **0** passing square predictions at evaluated checkpoints | The transient **0.844** squareness at 1,000 updates came from spurious, roughly **82%** foreground outputs, not valid squares. |
| Same README | Five-curve reference-cosine LR, 5,000 updates | **0/20** correct-condition outputs passed at 5,000 updates; final reported epsilon MSE **0.001876** | The changed learning-rate schedule alone did not solve model collapse. |
| [Authors' checkpoint control](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/pretrained_checkpoint_control.md) | Released pretrained checkpoint, 25 DDIM steps, one attempt each on 20 curves from 10 H groups | **7/20 (35%)** total; study-seen **4/10 (40%)**, study-held-out **3/10 (30%)** | Small **project-specific binary diagnostic**, not authors' Table 1 replication; checkpoint trained across the studied H range, so not held-out-H generalization. |
| [Evaluation protocol](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/evaluation.md) | Project-defined binary evaluator on 1,000 geometrically valid constructed target masks | **969/1,000 accepted (96.9%)**; **31/1,000 rejected (3.1%)** | Raster/threshold false rejections exist; do not portray binary scoring as ground truth about geometric validity. |
| [WACV 2027 accepted work](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/README.md) | Eight-stage ProxSCI-8, 256 precision schedules, 3 high-precision stages | OSM operator-visible regret **2.7%**, best global-static **6.3%** | WACV result; not a new CVPR experiment and not denoiser-stage skipping. |
| Same WACV README | Separate A100 native latency protocol | **23.6 ms** FP16 reference vs **16.4 ms** selected schedule (**1.44×**, **7.2 ms** saved) | Latency and quality findings used **different precision protocols**; do not present as one matched quality–speed data point. |
| [Incomplete-curve diffusion README](https://github.com/chaewon-research/diffusion-missing-curve-experiments/blob/main/README.md) | Three-seed full-data vs fixed-gap sine generation; gap-occupancy statistic on all generated points | DDPM full **13.80 ± 0.97%**, gap-trained **1.15 ± 0.38%**; DDIM full **13.97 ± 1.74%**, gap-trained **1.20 ± 0.45%** | Full-data control sees the evaluation region. These percentages are **not** completed-curve success rates. DDPM used **300** reverse steps; DDIM **50** — costs unmatched. |
| [QDC reproducibility README](https://github.com/chaewon-research/qdc-fractional-neural-operators/blob/main/README.md) | Validation-selected rank budgets at spatial sizes 32, 64, 128 | Audited selected ranks **K = 82 / 150 / 200**; five-run Cylinder validation described | Numerical operator results are **not** automatically vision accuracy, hardware speedup, or CVPR novelty. |

**DERIVED, NOT NEW EXPERIMENTS:** 7/20 = 35%, 29/50 = 58%, 31/1,000 = 3.1%, and 23.6/16.4 ≈ 1.44. Ratios and percentages are arithmetic restatements of repository-reported counts, not independent replications. With n=20, a 35% success statistic is highly uncertain; do not use it to claim strong generalization. Likewise, zero successes in 10 or 20 attempts does not establish a zero underlying probability.

### 8.2 Original geometric-solver publication — VERIFIED-EXTERNAL (NOT our replication)

[Original CVPR 2026 paper, Goren et al., Table 1 and Table 4](https://arxiv.org/html/2510.21697), original authors' measurements:

| Evaluation | Before snapping | After snapping | GT / control |
| --- | --- | --- | --- |
| Pixel-space squareness Q (higher better) | **0.892** | **0.891** | **0.924** GT raster |
| Pixel-space mean negative corner-distance alignment A (higher better) | **−1.60 px** | **−0.90 px** | **−0.14 px** GT raster |
| Parametric-space squareness Q | **0.880** | **0.879** | **1.000** continuous GT; **0.919** raster GT |
| Parametric-space alignment A | **−1.65 px** | **−1.17 px** | **0.00 px** continuous GT; **−0.27 px** raster GT |

The **goal of P0-02 is to reproduce these reported quantities**, not to fill a results table by copying them into the "ours" column. The project's binary success threshold (Q ≥ 0.85 and maximum corner distance ≤ 3 px) is *not reported as Table 1* and is not equivalent to the paper's original means. P0-02 remains **NOT MEASURED** on the authors' exact released evaluation set until an archived run exists.

### 8.3 Strong published acceleration work — VERIFIED-EXTERNAL (NOT apples-to-apples)

| Primary source | Published numerical point | Interpretation |
| --- | --- | --- |
| [SeaCache original project/results, CVPR 2026](https://jiwoogit.github.io/SeaCache/) | FLUX.1-dev, 50-step baseline: **20.9 s**; SeaCache δ=0.3: **9.4 s**, **PSNR 26.28 dB**, **LPIPS 0.106**, **SSIM 0.893**, measured versus a full-step output reference | Roughly **2.22× latency ratio** in *text-to-image FLUX*; NOT a target to claim or copy for geometric solving. |
| Same SeaCache source | FLUX δ=0.6: **6.4 s**, PSNR **21.33 dB**, LPIPS **0.226**, SSIM **0.798** | Illustrates **non-perfect trade-offs**: stronger acceleration can degrade reference fidelity. |
| [DPCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Cui_Denoising_as_Path_Planning_Training-Free_Acceleration_of_Diffusion_Models_with_CVPR_2026_paper.html) | Authors report a **4.87×** FLUX speedup operating point, with **+0.031 ImageReward** relative to prior acceleration methods | Different backbone, quality metric and setup; use only as a novelty/competition reference, not an expected curve-solver score. |
| [SenCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Haghighi_SenCache_Accelerating_Diffusion_Model_Inference_via_Sensitivity-Aware_Caching_CVPR_2026_paper.html) | Per-sample sensitivity-aware caching, published on Wan2.1, CogVideoX and LTX-Video | Methodologically relevant; do not invent a comparable geometric-solver number. |
| [CVPR 2027 author guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines) | **8** main-text pages excluding references/LLM statement; paper enrollment **Nov 10, 2026**; full paper **Nov 16, 2026**; supplement **Nov 23, 2026** (see call for papers) | Requirements, not measured performance. Author guidelines specifically flag fabricated content as desk-rejection grounds. |

**Cross-task disclaimer:** This literature sets the seriousness of the field. Nothing here implies that a proposed geometric-solver method will achieve 2×, 4×, or state-of-the-art acceleration, or that the error/quality metrics transfer.

## 9. Numerical completion specifications for EVERY backlog action — TARGET-ONLY, NOT MEASURED

These are **pre-registered planning choices and minimum reporting requirements**, **not predicted measurements**, **not scores to paste into a manuscript**, and **not official CVPR thresholds**. They should be modified only for documented feasibility/statistical reasons **before examining final holdout data**. Record actual results regardless of whether they miss targets.

### 9.1 P0 blockers — concrete numbers / fields to add

| ID | Concrete completion specification, proposed now | Current measured status |
| --- | --- | --- |
| P0-01 | Baseline ledger has **1 pinned upstream commit** (ca949551b1a811ac6dfe96e231a94f7e8105de46), **1 checkpoint file hash**, **1 dataset revision/hash**, **1 evaluator hash/patch log**, explicit **25 DDIM steps** and schedule first_mid_last:20,3,2. | Configuration source documented; exact run hashes to be captured. |
| P0-02 | **20** original-dataset samples for smoke test; if working, **at least 200** original-dataset evaluation examples or the authors' exact reported split if accessible. Save attempt-level rows. Published reference: raw Q **0.892**, raw A **−1.60 px**, snapped Q **0.891**, snapped A **−0.90 px**, GT Q **0.924**, GT A **−0.14 px**. Compare without falsely expecting exact numerical agreement; report sample CIs and data differences. | Original Table 1 reproduction **NOT MEASURED** here. |
| P0-03 | Provenance table covers **4 major axes**: input distribution/size, noise/sampler schedule, optimizer+batch/update protocol, scoring/snapping. Note paper appendix and released code can conflict. Specifically document **100** diffusion steps and **128×128** images as in the paper, separately from evaluation's **25** DDIM steps. Record patched evaluator hash. | Paper/code audit documented; running comparison pending. |
| P0-04 | Publish **6** pixel-space statistics per evaluation (raw and snapped Q/A, GT Q/A); add **8** parametric figures (pred/snap Q/A; GT and raster-GT Q/A) where coordinates exist. Binary project pass: Q ≥ **0.85**, all corners ≤ **3 px**. | Original paper metrics known; study binary metric reported separately. |
| P0-05 | Review **all 31 rejected** constructed-target masks from the known-valid set (not a random subset). Present **1,000/1,000** case-level audit, error causes, max/mean corner distances and threshold-sensitivity grid (for example Q=**0.80/0.85/0.90**, maximum distance=**2/3/4 px**). Freeze primary metric before final experiments. | **969/1,000** accepted; failure causes not fully quantified. |
| P0-06 | Report separate statuses for historical pilot conditions: **1** curve / **50** draws (29 passed); **5** curves / **5,000** updates; epoch **30 vs 40**; loss/LR ablations. Initiate **0** new unmotivated sweeps until baseline is reproduced. | Failures and control experiments documented. |
| P0-07 | Always label **7/20**, **4/10**, **3/10** as released-checkpoint *small custom dataset control* at **25** steps; label custom **0/20** results with their actual **25 or 99** step protocols. Never make a common success-ratio plot without matched settings. | Source results exist, not matched. |
| P0-08 | A standalone held-out-H study has **5 seen H groups (6,10,14,18,22)** and **5 held-out groups (8,12,16,20,24)**, **100** curves/group (**500/500**). It is an OOD generalization study, **not a qualifying computation-preservation paper** unless C/I/P/T added and measured. | Data generation/evaluation protocol documented; qualified cost-preservation result **NOT MEASURED**. |
| P0-09 | A **five-column overlap audit**: task/data, internal variable/intervention, algorithm, accuracy/cost protocol, scientific claim, comparing any candidate with accepted WACV. Include WACV **2.7% vs 6.3%** regret and separate **16.4 vs 23.6 ms** timing correctly labeled. | Existing WACV results reported; new nonoverlapping claim not demonstrated. |
| P0-10 | **All coauthors**: complete OpenReview by **Nov 10, 2026**; paper ≤ **8** main pages excluding references and LLM Usage Statement; submission **Nov 16**; supplement **Nov 23**, AoE. Include exactly **one explicit LLM Usage Statement section** identifying AI research/writing use truthfully. | Administrative compliance **NOT VERIFIED**. |
| P0-11 | For **each** candidate: **4** C/I/P/T answers, **≥3** directly relevant prior papers where available, **≥1** public executable baseline, **≥1** controlled falsification, **≥1** cost measure, **1** explicit stop rule. **3** prior papers is a screening target, not evidence that novelty is clear. | Decision criteria specified; no new method validated. |

### 9.2 P1 additions — concrete measurement grid and CONDITIONAL targets

| ID | Proposed experimental size / performance target / minimum reporting | Required result status |
| --- | --- | --- |
| P1-01 | Start with **25** full DDIM steps and fixed lower-compute budgets **20/15/10 denoiser evaluations** only where technically meaningful; compare full, uniformly spaced, random matched-budget, and critical-computation-preserving policies on **the same images/seeds**. Feature/block ablations must specify layer IDs and actual executed kernels. | **NOT MEASURED**. NFE comparison does not itself prove latency saving. |
| P1-02 | Report raw and snapped Q/A; max corner distance; binary pass Q≥**0.85** and max-distance≤**3 px**; full per-attempt success and best-of-k for **k=1/3** (label k accurately). Nondegeneracy: preregister minimum side length from observed target distribution rather than fabricate a universal px threshold. | **NOT MEASURED** for any compute-reduced new method. |
| P1-03 | Preliminary **target**: **15–30% real median end-to-end GPU latency decrease** at matched inputs, while avoiding more than **5 percentage points absolute** degradation in project success rate (or alternatively a preregistered bound on continuous Q/A). Controller overhead **target ≤5%** of end-to-end baseline latency. These are engineering **go/no-go hypotheses**, not evidence of a CVPR-level win. Report p50/p90, warmup ≥**20** iterations, repetitions ≥**30** per condition if feasible, device, batch, precision and memory. | **NOT MEASURED**. If savings disappear after controller overhead, stop practical speedup claim. |
| P1-04 | At least **1** faithful published caching/sampling baseline if applicable; also compare **uniform** and **random**. Prefer a **3–4 operating-point** latency–success frontier (25/20/15/10 NFE where applicable). Include SenCache, SeaCache, SVD-Cache, DPCache and TAP in related-work analysis; **only run methods compatible with the actual U-Net checkpoint**. | **NOT MEASURED**; literature numbers on FLUX/video are not geometric-solver baselines. |
| P1-05 | Select **≥3** candidate internal computations/representations (e.g., named U-Net resolutions/blocks), include **1** negative control module, and collect per-instance paired counterfactual damage. Report whether proposed criticality ranks outperform naive feature-norm/gradient or random controls. | **NOT MEASURED**; output preservation alone cannot prove internal preservation. |
| P1-06 | Staged pilot: up to **20 curves per H group ×5 H groups =100 curves** from development-only cohorts, with **2** fixed seeds/curve (**200 attempts/policy**). Locked evaluation: **100 curves ×5 held-out H groups ×3 seeds =1,500 attempts/policy**, *only if GPU budget allows*, and a matched seen-group report. Never tune on held-out group measurements. | **NOT MEASURED**; 1,500 attempts is a sampling plan, not observed data. |
| P1-07 | **1** secondary geometric task/model if a released, reproducible baseline exists; at least **100** distinct development samples and a separate holdout. If this is infeasible, claim only one-task evidence and do not invent generalization. | **NOT MEASURED**. |
| P1-08 | Every proposed scientific claim gets **≥1** directly supporting figure/table, **1** configuration/commit identifier and exact n; primary manuscript uses ≤**8** main pages. Keep raw failures/secondary grids in supplement. | Paper **NOT WRITTEN / NOT VALIDATED**. |
| P1-09 | Aim for **≥3** independent stochastic seeds on final evaluation where feasible; report paired, curve-clustered **95% bootstrap CIs** (for example **2,000** curve-level resamples), seed-level results, and denominators. For initial small n, show uncertainty rather than insisting on "significance." | Confidence intervals **NOT MEASURED**; do not mistake correlated seeds for independent curves. |
| P1-10 | **One mandatory novelty table**, with columns question, critical internal object, intervention, model/task, computational budget, primary evaluation metric, scientific difference; compare proposed work to WACV and at least **3** most related 2026 papers. | Distinct novelty **NOT ESTABLISHED**. |

**Interpretation of the proposed 15–30% / ≤5 percentage-point target:** This is a *screening rule*, neither an estimate of achievable performance nor a guarantee of conference competitiveness. A pretrained control currently reported only **35%** project-specific success on 20 samples; that baseline is too small/noisy to treat a 5-point drop as meaningful. Establish a reliable full-compute success distribution *first*, then use paired CIs and a preregistered noninferiority margin. Never select thresholds after seeing held-out results.

### 9.3 P2 archival items — numerical completeness expectations

| ID | Proposed minimum quantitative record | Current reality |
| --- | --- | --- |
| P2-01 | Preserve **3-seed** gap occupancy means ± SD, **300-step DDPM / 50-step DDIM** protocols, fixed gap location, and **2,000** generated points per run. Never claim gap completion based on percent occupancy alone. | Reported in incomplete-curve README. |
| P2-02 | If resumed, preregister **≥3** gap intervals (position and width) and **≥5** seeds across at least **2** denoiser architectures; compare **matched NFE and actual latency**, not unmatched DDPM/DDIM. | Proposed; **NOT MEASURED**. |
| P2-03 | Carry over QDC verified **K=82/150/200** only with their respective 32/64/128 settings and protocol; run **≥3** independent visual-model seeds for any truly distinct future study. | Existing QDC record is not evidence for a new CVPR visual experiment. |
| P2-04 | Keep WACV **2.7% vs 6.3%** operator-visible regret and **16.4 vs 23.6 ms** A100 latencies in **separate** tables or explicitly separated protocols. | Verified from WACV README; do not combine. |
| P2-05 | Require a manifest with **1** checkpoint hash per model, **1** source commit per codebase, each dataset version, seeds, GPU model, library versions and evaluation commands. Retain **all** raw per-case outputs, subject to storage/license limitations. | Partially present across repositories; an audit of each binary artifact is pending. |
| P2-06 | Maintain **0** fabricated experimental data points; **0** undocumented deleted negative trials; **0** unverified "SOTA"/"first"/"CVPR-ready" claims. Log count of failed runs and missing cases in every report rather than concealing them. | Integrity commitment, not a performance result. |

## 10. Prospective experimental result sheets — KEEP UNFILLED until a run exists

A prospective paper should include actual results at **multiple** compute budgets. This table is a measurement template; all cells are intentionally unfilled. **Never replace TBD with guessed numbers, "natural" noise, or extrapolations from unrelated papers.**

| Source/condition | n curves | Seeds per curve | NFE | Median GPU latency (ms) | p90 latency (ms) | Raw Q mean±SD | Raw alignment A (px) | Passes/attempts | 95% CI | Status |
| --- | ---: | ---: | ---: | ---: | ---: | --- | --- | --- | --- | --- |
| Released model, original-data replication | TBD | TBD | 25 | TBD | TBD | TBD | TBD | TBD | TBD | **NOT RUN IN THIS AUDIT** |
| Frozen full-compute solver on study curves | TBD | TBD | 25 | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Uniformly reduced compute | TBD | TBD | 20/15/10 | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Random matched-budget policy | TBD | TBD | matched | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Mechanism-preserving candidate | TBD | TBD | matched | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Applicable published caching baseline | TBD | TBD | matched | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |

**Capture schema (one observation per curve × seed × policy):** source commit; checkpoint and data hashes; curve ID; H group; split; noise seed; chosen compute policy and block IDs; actual NFE and skipped operations; raw/snap Q; raw/snap A; maximum corner distance; extracted corner count; pass/fail and reason; GPU SKU and precision; latency (ms); peak allocated/observed GPU memory (MiB); controller overhead (ms); execution status. Publish summary means **alongside** all per-case rows so real-world variation and negative cases remain visible.

**Do not engineer results to look "not suspiciously clean."** Report the authentic noisy distribution, including bad seeds, model collapse, unexpected latency reversals, missing cases and uncertainty. Healthy experimental reporting is not manufactured variance.

## 11. Practical and statistical stop rules — proposed, not established

1. **Before acceleration:** if author-checkpoint + documented compatibility-patched evaluator cannot approach original Table 1 Q/A on genuine original-dataset cases, stop all new selective-compute claims and debug baseline fidelity. A pilot diagnostic band of **±0.03 Q** and **±0.5 px A** versus the publication can trigger an investigation; **these are not pass/fail significance levels or required exact replication tolerances**. Full sample matching is preferable to any universal band.
2. **Before optimization:** if full-compute geometric success is low or highly heterogeneous across H groups, do not compare a policy on only the few passing curves. Report all samples and decide whether the study is scientifically powered to evaluate noninferiority.
3. **Before "capability-critical" claim:** if targeting the hypothesized internal blocks does not outperform naive or random compute allocation at matched measured cost, the criticality mechanism is unsubstantiated; revise or stop.
4. **Before "efficient" claim:** if real measured end-to-end acceleration is ≤0 once controller overhead is included, report a negative speedup result; do not substitute FLOP savings to claim actual inference speed.
5. **Before CVPR recommendation:** if no independently supported novelty difference from accepted WACV work and SenCache/SeaCache/SVD-Cache/DPCache/TAP exists, or no credible full-compute geometry baseline exists by the scientific go/no-go date, do **not** force the submission. A **competitive** published result is a literature comparator, not a license to invent equally impressive numbers.
6. **Integrity:** CVPR 2027 guidelines explicitly warn that fabrication, including obvious factual fabrication and invented citations, may trigger desk rejection. The user and human coauthors remain responsible for claims; include truthful LLM usage disclosures.

**Outcome on the date of this amendment:** verified reference and repository numbers are now recorded; **new compute-preservation experimental results remain unmeasured**. That is the correct scientific status, even if it looks less impressive than a fictional score table.
