# CVPR 2027: Acceptance-Oriented Execution Blueprint
**Created:** 2026-10-22 · **Status:** research execution specification, **not** a finished paper or a record of a new acceleration experiment.  
**Decision:** **NO speculative pivot; prioritize a bounded falsification study on the working, released geometric-solver checkpoint.** If the distinctive mechanism fails, do not force this project into a CVPR submission.  
**Change scope:** A **new standalone file** consolidating and replacing *planning advice*, **not** any existing experimental files, manuscripts, checkpoints, or negative results.

> **The one nonnegotiable research theme (verbatim from the [GitHub profile](https://github.com/chaewon-research/chaewon-research/blob/main/README.md)):**  
> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

The goal is **scientific acceptance competitiveness**, not aesthetically competitive tables. No numeric result is to be made up, perturbed to resemble natural noise, copied from another model into "ours," or cherry-picked. This blueprint keeps **[OBSERVED–OWN]**, **[PUBLISHED–OTHER]**, **[DERIVED]**, **[TARGET–PROPOSED]**, and **[TBD / NOT MEASURED]** apart. Proposed targets are *decision thresholds*, not predicted outcomes, fabricated results, official acceptance requirements, or promises of novelty.

---

## 1. One-page decision: what paper could actually satisfy the theme?

**Conditional scientific question (NOT yet a demonstrated contribution):**  
Can an *independently estimated, geometry-capability-specific* criticality map identify U-Net computations that must be refreshed rather than reused across denoising time, such that a frozen visual geometric solver retains constraint satisfaction at lower **measured end-to-end inference cost** than competent generic sensitivity, uniform caching, and random matched-budget policies?

**C — Cost.** Reduce actually executed **U-Net block computation**, not just nominal NFEs/FLOPs. Record hardware end-to-end wall time with controller and cache overhead included. Keep the **25 DDIM steps fixed initially**, so denoising-step skipping does not confound the internal-computation test.  
**I — Internals.** Precisely identified conditional/residual/decoder operations and time-specific intermediate activations; test whether their criticality for valid geometry differs from feature-norm/feature-error or output-similarity scores. Do not claim representation preservation without interventions that isolate such representations.  
**P — Capability.** Geometric square validity on the conditioning curve (continuous squareness, signed alignment, nondegenerate side length, optional binary criterion), reported separately from image similarity to one target or aesthetically good masks.  
**T — Counterfactual test.** Perturb/replace named internal features at held-fixed input/noise/timestep; estimate per-instance geometry damage; preselect "protect these operations" on a development split; compare on distinct curves **at matched measured GPU latency** against random, uniform, and generic-sensitivity policies; use a compatible published caching baseline if feasible. Predefine a stop rule.

**Theme verdict:** **PASS as a falsifiable proposal / NOT EMPIRICALLY VALIDATED.**  
**Novelty verdict:** **OPEN / high overlap risk** with existing sensitivity-aware, content-aware and subspace-aware diffusion caching.  
**CVPR readiness:** **NOT ESTABLISHED.** Do not turn this into a title promising a proven geometry-specific mechanism before the intervention experiment.  
**Paper rejection trigger:** If the purported geometry-specific ranking offers no reproducible added predictive value or better measured capability–cost frontier, **do not recommend this as the CVPR submission**, even if generic caching makes the model faster.

**Already-solved vs unsolved:** The authors' pretrained **inference/evaluation** now has a credible preliminary reproduction. **Do not repeat it as if missing.** A *new* efficient inference method and its causal novelty remain untested. The user's separately trained models still fail and are **not** appropriate baselines for performance preservation.

---

## 2. Observed numerical evidence ledger — accurate denominators and provenance

### 2A. Own repository: verified/documented findings (not measurements made for this blueprint)

Source: [preliminary original-checkpoint replication report](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/official_square_table1_preliminary_results.md), [latest project README](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/README.md), [checkpoint calibration](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/checkpoint_calibration_results.md).

| Provenance and protocol | Value | Interpretation / caveat |
|---|---:|---|
| **[OBSERVED–OWN]** Authors' checkpoint; 200 examples from released 100k-pair dataset; 25-step DDIM, raw pixel Q | **0.8988** | Inference reproduction; paper reports **0.892** on its evaluation. Not full-data evaluation or training replication. |
| Same 200 examples; raw **positive** mean corner distance | **1.4131 px** | Paper reports **1.60 px**; original paper's signed alignment is **−1.60 px**. Positive distance and signed alignment use opposite conventions. |
| Same 200; *pixel-snapped* Q | **0.8803** | Paper snapped **0.891**; snapping does not automatically maximize Q. |
| Same 200; pixel-snapped mean corner distance | **0.6847 px** | Paper snapped distance **0.90 px**. |
| Source GT-raster 200-example Q / corner distance | **0.9258 / 0.1525 px** | Paper GT raster Q **0.924**, distance **0.14 px**. |
| Pixel-snapping per-example distance changes | **167 improved / 15 unchanged / 18 worsened** out of **200** | Do not select only improved examples. |
| 200-example bootstrap marginal 95% ranges (descriptive) | Raw Q **[0.89179, 0.90535]**, raw distance **[1.24933, 1.58408] px** | 18,000 bootstrap resamples of existing data. Not a statistical equivalence claim or new experiment. |
| Released-checkpoint original-data source | **100,000** pairs, **128 × 128 px**, 25 DDIM steps, seed **42** for evaluation | Checkpoint config encoded 150,000 samples; released archive has 100,000. Record override. |
| Compatible evaluation source | Original commit **ca949551b1a811ac6dfe96e231a94f7e8105de46**; patched-evaluator SHA-256 **81b97077e443659dbaa91f5aa5546116900e2d7b9124bbe7ac30926714116c7c** | Original evaluator requires a documented import and empty-contour compatibility repair. It is **not unmodified** upstream. |
| Original archive metadata issue | **20-example smoke test equals first 20 of the 200 rows** | Not 220 independent samples. Exact original training/evaluation exclusion is not proven by these archived CSV IDs. |
| **[OBSERVED–OWN]** Same-code calibration, 4 original-data curves × 2 seeds, released model 25-step Q | **0.88808** | Tiny positive control; no snapping; not original Table 1. |
| Same calibration, custom 5,000-update model, 25-step Q | **0.02863** | Failed learned generation. At 99 steps the custom Q was **0.01357**, not a sampler-step rescue. |
| Same calibration, conditioning-swap output MAE, normalized pixel units | Released **0.51509**, custom **0.02595** | Not a normalized causal dependency measure; scale of outputs differs. |
| Custom training, original 100k source distribution, effective batch 4, 5,000 optimizer updates | **0/16** passes at each of 1k/2k/5k | Failed budget-limited training; not evidence that authors' large-scale training cannot work. |
| Earlier 5-pair training and 5,000-update variants | **0/10** train and **0/10** separate seen-validation in reported tests | Preserve negative results; not the main efficiency baseline. |
| One-pair memorization 1k-update experiment | **29/50** attempts passed on *one training curve* | Pipeline memorization; not generalization. |
| Authors' broad-trained checkpoint on separate small custom H-group sample | **7/20** project-defined passes, 25 DDIM steps | **NOT** published Table 1, **NOT** held-out-H generalization: H groups lie in pretrained distribution. |
| Project raster binary evaluator test | **969/1,000** known-valid target masks passed | 31 false rejections are a metric caveat; project binary success is not exact geometric truth. |

**Do not conflate:** source 200-example Q vs small H-group 7/20 success; released checkpoint vs custom 5k checkpoint; pixel-space scores vs pseudo-parametric fallback columns (original archive lacks actual continuous point metadata); validation subjects vs source training exclusion. The independently checked 200-example archive was recomputed from uploaded CSVs; the checkpoint and dataset bytes were not independently reexecuted during that check.

### 2B. Accepted work and published competitors (source numbers, NOT ours)

| Source | Reported finding | Strict comparison limit |
|---|---|---|
| [Accepted WACV 2027 OSM](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/README.md) | **2.7%** normalized operator-visible regret vs **6.3%** global static at three high-precision stages; separate native A100 **16.4 ms vs 23.6 ms** FP16 reference, **1.44×** ratio | Precision and timing use distinct protocols; do not present as one matched accuracy/speed point or reuse as a new CVPR result. |
| [Goren et al., CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Goren_Visual_Diffusion_Models_are_Geometric_Solvers_CVPR_2026_paper.html) | Original raw Q **0.892**, signed alignment **−1.60 px**; snapped Q **0.891**, alignment **−0.90 px**; GT raster Q **0.924**, alignment **−0.14 px** | This is the existing geometric-solving method, not our efficiency result. |
| [DPCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Cui_Denoising_as_Path_Planning_Training-Free_Acceleration_of_Diffusion_Models_with_CVPR_2026_paper.html) | **4.87×** speedup/+**0.031 ImageReward** *relative to prior acceleration methods* at a FLUX operating point; other reported operating points differ | DiT/FLUX; not a U-Net square-solving result; no direct numeric equivalence. |
| [SVD-Cache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chen_Forecast_the_Principal_Stabilize_the_Residual_Subspace-Aware_Feature_Caching_for_CVPR_2026_paper.html) | Reports **5.55×** speedup on FLUX/HunyuanVideo settings | Transformer architecture; subspace-aware reuse already prior art; not a geometry benchmark. |
| [SeaCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chung_SeaCache_Spectral-Evolution-Aware_Cache_for_Accelerating_Diffusion_Models_CVPR_2026_paper.html) | Spectrally filtered feature-difference cache selection | Generic feature significance by spectral content is prior art. No cross-model numeric score imported. |
| [SenCache, CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Haghighi_SenCache_Accelerating_Diffusion_Model_Inference_via_Sensitivity-Aware_Caching_CVPR_2026_paper.html) | Input/timestep sensitivity-aware reuse, per-sample | Generic sensitivity modeling is prior art. Claim must be beyond "sensitivity matters". |

**Important:** Extremely large acceleration ratios on image/video diffusion transformers are *not* fair benchmark targets for this released **small conditional U-Net**. Real acceptance strength hinges on (a) a distinct verified mechanism, (b) a competent architecture-matched speed/quality frontier, and (c) transparent generality limitations. No invented 2×/5× geometric solver results.

---

## 3. Numerical goals: realistic *research targets*, not experimental results

The initial baseline estimate for interpreting quality is the reported original-data **Q ≈ 0.8988** and mean raw corner distance **≈ 1.4131 px** from a 200-example frozen-pretrained inference run. These are **not** a paired baseline for the new policy until the same held-out curves and noise seeds are run under each policy.

| Measurement | [TARGET–PROPOSED] first useful pilot | [TARGET–PROPOSED] stronger main result | Status and reason |
|---|---|---|---|
| Full-cost reference | Fixed **25-step** DDIM, frozen released weights | Identical full model under matching CUDA/precision/batch | **Existing correctness anchor, GPU latency TBD.** |
| End-to-end speed ratio vs identical full model | **≥1.10–1.15×** to justify scaling beyond a smoke test | **≥1.25×** and preferably a credible **1.35–1.50×** operating point if kernels actually permit it | **Not measured;** if a method only saves FLOPs, do not claim these ratios. |
| Raw pixel-space squareness Δ vs paired full | Investigate if mean loss exceeds **0.015** | Exploratory noninferiority target: mean loss **≤0.010 absolute** | **Not measured.** 0.8988−0.010=**0.8888** is arithmetic illustration only, not an "ours" result or universal threshold. |
| Positive raw corner distance increase | Investigate if mean increase exceeds **0.25 px** | Exploratory target: **≤0.15 px** mean increase | **Not measured.** 1.4131+0.15≈**1.5631 px** arithmetic, not a fabricated experimental average. |
| Snapped Q / corner distance | Measure separately; do not hide declines | Evaluate each under its **own paired full-compute reference** | Already observed snapping lowered Q while improving alignment; no target guaranteeing improvement on both metrics. |
| Binary geometric validity | Report *full-vs-policy paired counts*; don't silently drop non-scorable masks | Seek no material loss; provisional absolute margin **3–5 percentage points** **only if justified by pilot variance and evaluation n** | **Baseline rate on the original 200 examples not verified in the evidence ledger.** Do not treat 7/20 custom dataset as that rate. |
| Policy vs strongest equal-latency baseline | Any consistent benefit after paired inspection | Positive paired advantage in Q/alignment and/or valid-square success with appropriate uncertainty | **Not measured.** A raw speed increase alone does not establish novel geometry-specific selection. |
| Controller/recompute overhead | Profile explicitly | Favor designs whose overhead is a **small fraction of saved computation**, engineering screening preference **<10% of baseline inference latency** | **Not measured;** do not arbitrarily subtract overhead from reported time. |
| Coverage of negative examples | **100% recorded**, including failed mask extraction and OOM/error attempts | **100% recorded** | Reporting-integrity requirement, not a performance target. |

**What "competitive" means here:** **measured Pareto improvement over strong *applicable*, latency-matched policies** plus a mechanism-specific finding. A 1.4× hypothetical speedup alone is not conference competitiveness. An appealingly irregular result table is not required; **never inject variance, tune to a pleasing number, or invent per-seed scores**. Expected data can be messy; record them all.

**Pre-registration rule:** Use these only as *pilot decision hypotheses*. Before final locked evaluation, set final noninferiority margins based on task utility and observed *development-set* paired variability. Do not shrink/expand margins after observing holdout. Report confidence intervals, not only thresholds.

---

## 4. Full experiment design: smallest units, then scale only on success

### 4.1 Assets and population lock (do first)

- **T01** Verify frozen authors' checkpoint hash: \`51f8cee68c64ab662801d8bd46f29d7f4d88c8d0fe072a4624776a5d1dd85f0f\`; source ref \`ca949551b1a811ac6dfe96e231a94f7e8105de46\`.
- **T02** Verify released original archive hash: \`68c9a6bec7ee375ffdd0c90f4a60115a1b9bb9650adc7247abf5518e339e52b6\`. If unavailable, record "unverified" rather than inventing a check.
- **T03** Reuse the already-verified 200-example summary as historical evidence; **do not present its nested 20-example run as independent**.
- **T04** Inspect the patched evaluator and its digest; preserve the compatibility-patched label; assert metric formula provenance.
- **T05** Define *new* experiment split by **source curve identifier**, not evaluation iteration index. Original checkpoint train/eval overlap remains unverified unless traceable source identifiers prove otherwise.
- **T06** Dev pilot: **40 distinct curves × 2 independent noise seeds = 80 paired inputs**, where feasible. Use them for intervention selection only.
- **T07** Final primary evaluation: **200 distinct curves × 2 seeds = 400 attempts per policy** as the starting capacity plan; choose sample size after pilot variability and compute profiling. Lock and prohibit calibration on this evaluation set. Distinguish 200 independent curve clusters from 400 correlated attempts.
- **T08** Optional geometry-stratified extension: 5 H groups × 40 curves/group × 2 seeds = 400 attempts *if* those groups are correctly defined and the checkpoint's training coverage is disclosed. **No claim of held-out-H generalization for broad-trained released weights.**

### 4.2 Latency sanity: do not optimize a non-bottleneck

- **T09** Profile **1** batch-1 and **1** representative batched inference mode separately on the actual GPU; do not equate T4 and A100 timings.
- **T10** Break down time: encoder / conditional down blocks / mid / decoder / sampling overhead / scoring / controller; report exactly which part is on the critical path.
- **T11** Warmup **≥20** repeated full-model calls before measurement. Prefer **≥100 timed calls** per main configuration when affordable; record every latency sample. Synchronize CUDA events or wall-time boundaries accurately; exclude one-time weight-loading from steady-state latency but report it separately if deployment relevance requires.
- **T12** Report median/p90 end-to-end sampling, hardware and library versions, batch size, precision, peak CUDA memory and confidence bounds. Controller and feature-cache memory costs count.
- **T13** Abort "faster" claims if kernel launches, cache movement or dynamic shapes erase nominal computation savings.

### 4.3 Mechanism probe — 1 model, 1 clear hypothesis

- **T14** Name **3–5** hypothesized critical internal components (e.g., specific conditional encoder stages, mid block, and decoder stages) based on *architecture inspection*, not on claimed discovered importance.
- **T15** On fixed dev curve × seed × DDIM timestep, substitute a component's internal activation with a *compatible* earlier activation or controlled low-cost approximation. Also test **zero**, **random**, and shape-matched control interventions; track whether interventions change parameter range/distribution.
- **T16** Measure per-intervention **ΔQ**, **Δpositive-alignment-distance**, output topology/foreground sanity, binary valid-square changes, and **Δfeature reconstruction error**. Store each per-instance outcome, including non-scorable outputs.
- **T17** Ask the novel scientific question: *Does ranking components by geometry damage differ reproducibly from ranking by generic output/activation perturbation or denoiser MSE?* Compare **Spearman rank agreement** and **predictive out-of-development agreement**; **actual correlation values TBD**, not assumed.
- **T18** Use one **negative-control** component, one generic activation-error predictor, and one random selection baseline. If geometry-specific ranking collapses to generic sensitivity, the claimed distinctness is not demonstrated.

### 4.4 Implement **actual** inference-time savings

- **T19** Keep **25 DDIM steps** initially. Change only whether specific expensive internal U-Net features are recomputed, reused or approximated. Count executed blocks and actual time.
- **T20** Use predetermined key-steps/refresh schedule first; only add content-dependent control if it beats its overhead and can be calibrated without holdout leakage.
- **T21** Test **3 operating points** after profiling: full model; approximately **10–15% target compute reduction**, then **20–30% target compute reduction** of the measured bottleneck block work. This is an engineering plan for choosing variants, **not** a claim of real wall-time saving.
- **T22** For each operating point run: **full**, **uniform**, **random**, **generic sensitivity**, and **geometry-specific policy**. Where possible add one **faithfully compatible published caching method**; otherwise explicitly mark architecture incompatibility rather than faking an implementation.
- **T23** Use **equal measured time**, or interpolate actual measured Pareto frontiers over multiple operating points; do not equate equal NFE/FLOPs with equal latency. Keep all methods on the exact same curves, noise seeds and geometry scoring.
- **T24** If output generation collapses under an intervention, report success as a failure with missing geometric measurements flagged, never quietly drop it and recompute means over survivors.

### 4.5 Final quality and inference

- **T25** Report raw Q, snapped Q, raw positive mean corner distance, snapped distance, all four maximum corner distances or maximum distance, foreground fraction and invalid-contour rate.
- **T26** Binary success is **study-only**, defined as **Q≥0.85** and *each* fitted corner ≤**3 px** from its curve. Report continuous metrics regardless; analyze the evaluator's **31/1,000** known-valid false rejections.
- **T27** Report **attempt-level** pass rate and optional **best-of-k** per curve separately; k=2 if exactly two noise seeds, no disguised best-of-3.
- **T28** On final paired outcomes compute curve-cluster bootstrap **95% CIs** (e.g., **2,000** curve-resampled draws) and paired success discordances; no independent-seed fiction. Report every policy budget and all failing examples.
- **T29** Perform Q threshold and corner-distance threshold sensitivity *as an auxiliary analysis*; freeze the primary binary criterion before final comparison. No significance claims from a selected favorable threshold.
- **T30** Make final verdict **GO/NO-GO** on (i) theme C/I/P/T, (ii) mechanism-specific benefit vs generic policies, (iii) real latency advantage, (iv) model's legitimate geometric capability, and (v) novelty against closest work.

### 4.6 Suggested raw result schema (create before running)

\`source_commit, checkpoint_sha256, dataset_sha256, source_curve_id, evaluation_split, H, noise_seed, solver_steps, inference_policy, selected_blocks, reuse_intervals, actual_executed_blocks, precision, cuda_device, batch_size, latency_ms, controller_ms, peak_memory_mib, raw_q, snapped_q, raw_mean_dist_px, snapped_mean_dist_px, raw_max_corner_dist_px, curve_valid_binary, reason_invalid, failed_execution, run_timestamp, config_sha256\`.

**No placeholder that looks like a measured score.** Missing / not-run is \`NA\` with a reason and a documented denominator.

---

## 5. Microtask matrix — best version of *every* previous backlog item

**Disposition:** DO NOW = important to test acceptance-worthy hypothesis; PRESERVE = already completed and should be documented, not rerun; CONDITIONALLY = after successful first intervention; DEFER = poor CVPR use of remaining time.

### P0: Grounding, provenance, submission safety

| ID | Disposition | Small executable elements | Best attainable state / completion evidence |
| --- | --- | --- | --- |
| **P0-01** Baseline | **PRESERVE + T01–05** | Pin checkpoint/source → verify hashes → lock 25 DDIM steps → capture evaluator patch → track source curve IDs | One immutable inference manifest; released working checkpoint, not failing custom model. |
| **P0-02** Reproduction | **PRESERVE** | Link 200-row results → preserve bootstrap → note nested 20 → avoid training reproduction claim | Raw Q 0.8988 / raw distance 1.4131 px honestly identified as preliminary 200-sample original-data inference replication. |
| **P0-03** Source fidelity | **DO NOW** | Diff evaluation helpers → verify patched import → record noise/batch configuration → keep code/hash table | No erroneous "unmodified evaluator" or paper/config equivalence. |
| **P0-04** Metric fidelity | **DO NOW** | Separate raw/snap → separate pixel/true-parametric → signed alignment vs positive distance → binary auxiliary | Original Table 1 comparable without mixing metric conventions. |
| **P0-05** Validator | **DO NOW, bounded** | Inspect 31 known-valid false rejects → failure types → threshold sensitivity → freeze metric | Honest binary validity and verified scorer limitations; prioritize before using pass rate as paper headline. |
| **P0-06** Failed training | **DEFER + PRESERVE** | Save 1k/2k/5k runs → record 0/16 and calibration → train fidelity audit separately | **Zero unmotivated retraining** as prerequisite to faster *released* model. |
| **P0-07** Comparisons | **DO NOW** | Distinguish 200 original samples vs 20 custom H samples → paired new data → no unmatched bar charts | One provenance-clean comparison table. |
| **P0-08** Hard theme gate | **DO NOW** | Complete C → I → P → T → reject merely better geometric generalization | The actual scientific question is computation-criticality and capability conservation. |
| **P0-09** Prior paper overlap | **DO NOW** | WACV: map task → intervention → method → benchmarks → compute protocol | No resubmission/relabeling of accepted operator-conditioned mixed-precision results. |
| **P0-10** Administration | **DO NOW, parallel** | Coauthor profiles → conflicts → reciprocal reviewer and author quota checks → enroll → anonymous paper → LLM disclosure | Meet Nov 10 registration and Nov 16 paper deadlines, Nov 23 supplement; verify all official rules in Section 8. |
| **P0-11** Novelty | **DO NOW** | SenCache / SeaCache / SVD-Cache / DPCache audit → matched controls → explicit difference & falsification | If "geometry-critical" gives no extra mechanism beyond known feature sensitivity, **NO-GO**. |

### P1: Scientific work that changes paper competitiveness

| ID | Disposition | Small executable elements | Best attainable state / completion evidence |
| --- | --- | --- | --- |
| **P1-01** Method | **DO NOW** | Block profile → candidate selection → controlled replacement → cache/reuse implementation → real saved kernels | Measured selective block approximation in the 25-step released solver. |
| **P1-02** Capability | **DO NOW** | Raw and snap Q/A → min side → invalid contours → paired binary pass → failure gallery | Preserve geometry-specific constraint satisfaction, not only RGB/mask similarity. |
| **P1-03** Hardware | **DO NOW** | GPU sync → warmup → repeat → latency p50/p90 → controller + memory → mixed batching protocols | Real end-to-end acceleration at a documented quality level, not FLOP-only speedup. |
| **P1-04** Competition | **DO NOW** | Uniform / random / generic sensitivity / paper-compatible cache → compare at matched measured time | Novel Pareto advantage over strong feasible baselines, with incompatible prior methods marked honestly. |
| **P1-05** Critical internals | **DO NOW FIRST** | Per-block intervention → predict Δgeometry → negative control → test ranking stability | A *causal, predictable* criticality mechanism, not post-hoc labels on successful images. |
| **P1-06** Generalization | **CONDITIONALLY** | Fix policy on dev → lock distinct original-data curves → optionally stratify H | Independent-instance efficiency transfer; no unjustified claim of unseen H groups for a broadly pretrained model. |
| **P1-07** Second task | **DEFER UNLESS MAIN RESULT POSITIVE** | Find pretrained solver → validate metrics → implement same selective policy | Generality only if time permits; do not lose weeks training an unrelated model. |
| **P1-08** Paper | **CONDITIONALLY** | One hypothesis → one main frontier → intervention proof → limitations → 8-page text | Every abstract result traceable to raw rows and published comparator. |
| **P1-09** Statistics | **DO NOW** | Independent curve clusters → fixed seeds → paired CIs → discordant cases → curve strata | Quantified uncertainty; **200 curves × 2 seeds** as provisional main evaluation, not 400 independent curves. |
| **P1-10** New vs WACV | **DO NOW** | WACV precision operator → proposed U-Net internal refresh → differing capability, intervention, data, cost metric | Claim truly distinct, not renamed stage sensitivity. |

### P2: Protect prior work; do not manufacture an expanded project

| ID | Disposition | Small executable elements | Best attainable state / completion evidence |
| --- | --- | --- | --- |
| **P2-01** Missing curves | **PRESERVE** | Retain negative missing-region outcomes → label outcome metric → no unsupported completion claim | Honest archived pilot, not an artificial strong CVPR baseline. |
| **P2-02** More missing-curve runs | **DEFER** | Additional gaps/seeds/models only after an independently justified paper need | Zero irrelevant GPU sweeps. |
| **P2-03** QDC | **PRESERVE** | Cite prior quantized-defect insight → separate domain/algorithm claims → no false novelty transfer | Existing foundation, not newly measured visual compute. |
| **P2-04** WACV | **PRESERVE** | Retain 2.7/6.3% regret and 16.4/23.6ms under different protocols | Accepted prior work cited accurately. |
| **P2-05** Reproducibility | **DO NOW** | Run logs → hashes → raw CSV → seeds → commit → environment → GPU spec | Reproducible core evidence and transparent failures. |
| **P2-06** Scientific claim hygiene | **DO NOW** | Audit "SOTA/first/faster/preserves/generalizes" → keep only backed claims | No altered, censored, extrapolated or fictional results. |

---

## 6. Reviewer-facing outputs that need to exist (and should not be faked)

| Manuscript component | Evidence that actually makes it strong | Status |
| --- | --- | --- |
| Working baseline table | Original checkpoint raw/snap metrics, exact evaluator/provenance, sample counts and bounds | **Preliminary existing evidence** |
| **Figure 1: mechanism** | Per-block intervention: geometry Δ vs generic activation Δ, paired negative controls, stability over curves | **TBD** |
| **Figure 2: main Pareto frontier** | Geometric Q/alignment/validity vs **actual GPU latency**, multiple operating points & competing policies | **TBD** |
| **Table 1: latency/capability** | Full, uniform, random, generic sensitivity, proposed, compatible published baseline, matched inputs | **TBD** |
| **Table 2: robustness** | Distinct curve clusters, multiple seeds, success discordances, failure cases, uncertainty | **TBD** |
| **Ablations** | Geometry-critical selector removed; important blocks disabled; refresh frequency; fixed vs dynamic | **TBD** |
| WACV novelty disclosure | Accepted WACV question, operator, method and results side-by-side with genuinely new contribution | **Required; not a score** |
| Limitations | Single task, potential checkpoint/data overlap, custom threshold false negatives, method overhead | **Known; update with new evidence** |
| Supplement | Scripts, data selection, hashes, per-sample/seed rows, GPU timing, negative results and LLM usage | **TBD** |

**Exact structure for manuscript argument:** (1) Why generic approximation can break *capability*, (2) measured internal causality, (3) computation-preserving selection, (4) real latency–capability improvement against equal-budget policies, (5) scope/limitations. **Do not write an affirmative title or abstract result before testing.**

---

## 7. Raw empty result table: insert real data only after inference

| Policy | Original curve IDs | Attempts | Actual full/reused block work | GPU latency p50/p90 (ms) | Raw Q mean (95% CI) | Raw dist px (95% CI) | Valid attempts / total | Paired Δ vs full | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Frozen released baseline | TBD | TBD | 100% / 0% | TBD | TBD | TBD | TBD | — | **NOT RUN FOR NEW PAIRED COMPARISON** |
| Uniform compute reduction | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Random matched compute | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Generic sensitivity policy | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Geometry-aware policy | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |
| Published compatible cache | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD | **NOT MEASURED** |

Published baseline Q and distance in Section 2 are **historical anchors, not placeholders** in this table. Do not substitute them for recomputed paired-full values. Keep invalid contours in success denominators; mark missing continuous metrics explicitly and analyze missingness.

---

## 8. CVPR 2027 administrative facts that affect acceptance probability

Official [Dates](https://cvpr.thecvf.com/Conferences/2027/Dates), [Call for Papers](https://cvpr.thecvf.com/Conferences/2027/CallForPapers), [Author Guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines):

- **Nov 10, 2026 AoE:** Enrollment, finalized author roster and each author's complete OpenReview profile. Profiles without institutional email may need moderation. No late author addition/removal.
- **Nov 16, 2026 AoE:** Main paper due, at most **8 content pages** (references and mandatory LLM Usage Statement excluded); correct double-blind formatting.
- **Nov 23, 2026 AoE:** Supplement deadline.
- **LLM Usage Statement:** mandatory after main text and before references; name AI tools actually used and affected parts of research/writing, accurately; omission can cause desk rejection.
- **Reciprocal reviewer:** CVPR 2027 has eligibility/reciprocal reviewer constraints. **Verify WACV 2027 acceptance appears in the relevant OpenReview profile if relying on it**; don't assume GitHub links alone establish eligibility. Check author quota/exception details against official guidelines.
- **Prior accepted/dual work:** WACV 2027 is accepted. A CVPR paper must not be substantially similar; declare and cite prior work according to anonymity and publication policies.
- **Contemporaneous work:** online after **Sep 15, 2026** generally receives contemporaneous consideration but still needs fair citation/discussion and non-plagiarism. No excuse to ignore close prior work.
- **Integrity:** actual experiments, authentic distributions, no invented citations or artificial "natural-looking" variance. Reviewers are not obligated to accept one-model incremental acceleration.

## 9. Locked calendar and stop rules (from 2026-10-22)

| Dates (2026) | What to finish | Decision |
| --- | --- | --- |
| **Oct 22–24** | Checkpoint/evaluator freeze; GPU block timing; 40-curve ×2-seed dev intervention sensitivity | If no coherent capability-sensitive computation and no feasible efficient implementation, **NO-GO**. |
| **Oct 25–28** | Implement low-cost block policy and generic controls; 2–3 measured operating points | If geometry-specific selection cannot dominate or complement generic sensitivity **at matched real latency**, **NO-GO**. |
| **Oct 29–Nov 5** | Only after positive pilot: distinct 200-curve ×2-seed primary test, paired CIs, one compatible published baseline, ablations | If effect unstable or speedups disappear after overhead, **NO-GO**. |
| **Nov 6–9** | Write defensible eight-page paper with truthful LLM disclosure; freeze figures, hashes, novelty table | Check desk-rejection/admin conditions. |
| **Nov 10 / 16 / 23** | Enroll / submit / supplement if scientific case is genuinely ready | **Do not submit an unvalidated claim merely to meet a date.** |

**Acceptance-optimal decision logic:** These dates are external deadlines, not a command to fabricate or polish away failure. If Oct 28 falsification fails, keep useful negative research and revise for another venue rather than burn the remaining time on a weak CVPR submission or pivot blindly.

## 10. Primary-source reference index (links checked in the literature review)

1. [Profile: exact overarching theme](https://github.com/chaewon-research/chaewon-research/blob/main/README.md).
2. [Original geometric solver — CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Goren_Visual_Diffusion_Models_are_Geometric_Solvers_CVPR_2026_paper.html).
3. [Our verified preliminary original-data reproduction](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/official_square_table1_preliminary_results.md).
4. [Our calibration and custom-training failures](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/docs/checkpoint_calibration_results.md).
5. [Our full geometric-solver research README](https://github.com/chaewon-research/visual-geometric-solver-generalization/blob/main/README.md).
6. [Our accepted WACV 2027 work](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/README.md).
7. [SenCache — CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Haghighi_SenCache_Accelerating_Diffusion_Model_Inference_via_Sensitivity-Aware_Caching_CVPR_2026_paper.html).
8. [SeaCache — CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chung_SeaCache_Spectral-Evolution-Aware_Cache_for_Accelerating_Diffusion_Models_CVPR_2026_paper.html).
9. [SVD-Cache — CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Chen_Forecast_the_Principal_Stabilize_the_Residual_Subspace-Aware_Feature_Caching_for_CVPR_2026_paper.html).
10. [DPCache — CVPR 2026](https://openaccess.thecvf.com/content/CVPR2026/html/Cui_Denoising_as_Path_Planning_Training-Free_Acceleration_of_Diffusion_Models_with_CVPR_2026_paper.html).
11. [CVPR 2027 Dates](https://cvpr.thecvf.com/Conferences/2027/Dates).
12. [CVPR 2027 Author Guidelines](https://cvpr.thecvf.com/Conferences/2027/AuthorGuidelines).

**FINAL INTEGRITY DECLARATION:** This file contains historical source measurements and prospective numerical targets only. **No new acceleration or capability-preservation experiment was performed to create it; its proposed effect sizes and 1.25×/1.5× scenarios are not measured results.** "Competitive" is not equivalent to flattering numbers. The acceptance case is conditional on a novel, reproducible, mechanism-specific finding plus measured hardware/capability evidence.
