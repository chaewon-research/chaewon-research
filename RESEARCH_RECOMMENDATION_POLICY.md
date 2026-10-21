# Research Recommendation Policy — Mandatory Hard Gate

**Status:** Binding research-idea recommendation criteria for this repository.

## 1. Canonical research theme (quote exactly)

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

Source of truth: the **Research Direction** section of [README.md](README.md). This overarching question—not an existing method, repository, collaborator, model family, or submission deadline—determines which ideas are eligible for recommendation.

## 2. Non-negotiable eligibility gate

Evaluate the actual **proposed scientific question and experiment**, not a broad subject-label or a plausible-sounding title. All four conditions must be explicitly present:

1. **Reduce cost (C).** Name a concrete cost to reduce: measured inference latency, energy, memory, bandwidth, number of model evaluations, or another clearly defined computational resource. FLOPs or proxy counts alone cannot substantiate a claimed real-world speedup.
2. **Identify critical internals (I).** Name the *internal computations or representations* hypothesized to be indispensable (e.g., particular layers, features, tokens, frequency components, arithmetic operations, or update steps). Specify why approximation/removal might damage the capability. Simply preserving the final output or measuring generic image quality is not sufficient.
3. **Preserve a capability (P).** Name a capability-level outcome and the acceptable degradation under reduced cost. Show why it captures what the model can *do*, not merely an appealing example or visual similarity score.
4. **Test the connection (T).** Specify a causal or counterfactual test: intervene on/approximate the proposed internal computation; measure capability changes; compare against a cost-matched, nonselective or existing selective policy; report actual cost and quality together. Controls must be reproducible.

**PASS (conceptual eligibility)** only if **C + I + P + T** are all clear and falsifiable. **FAIL** if any part is absent, vague, or bolted on after the topic was selected. Mark unperformed or inconclusive experiments **UNVALIDATED**; never treat conceptual eligibility as empirical confirmation.

### Examples of immediate rejection

- "Make diffusion faster" without specifying and testing indispensable internal computations.
- "Get better geometric solutions" without explicit computational reduction and internal preservation.
- "Prune important visual tokens" without a concrete capability-critical mechanism, counterfactual evidence, or a defensible distinction from prior pruning work.
- "Extend the accepted WACV paper" merely because the model or sensing task is familiar.
- "The method is novel/competitive because it satisfies the theme"; theme alignment alone does not establish either claim.

## 3. Selection process (never reverse the order)

1. **Quote the exact theme** from the README and state the C/I/P/T conditions.
2. **Generate candidates across the full eligible research space** (e.g., compression, neural architectures, efficient perception and reasoning, selective execution, numerical precision, representation preservation). Do not start by assuming that inverse problems, quantization, diffusion, or any particular prior repository is best.
3. **Apply C/I/P/T to each candidate before ranking.** Reject failures transparently. An idea cannot win based on venue popularity, convenience, or existing code if it fails the gate.
4. **Audit novelty against the closest prior work.** Identify at least the most relevant competing methods and explain which scientific claim remains different. Do not assert novelty is established from a superficial search; distinguish known precedents from a tentative open question. Prefer primary papers and official venue sources when checking current research.
5. **Verify available evidence.** Read current GitHub README/experiment logs, including negative results and baseline limitations; do not turn preliminary or failed experiments into a claim of feasibility. Explicitly separate proposed hypotheses, documented findings, and verified independently published work.
6. **Rank only eligible ideas** by scientific distinctness, measurable capability preservation, reproducible controls, real compute savings, strong baselines, venue fit, and time/compute feasibility. Call out overlap with existing/accepted publications, including WACV work.
7. **Recommend conditionally**, with one decisive low-cost falsification experiment, quantitative go/no-go criteria, and a backup path if it fails. Do not promise acceptance or claim a result before measuring it.

A tight deadline changes *feasibility*, not *eligibility*. It never licenses relaxing the hard gate or defaulting to the easiest familiar project.

## 4. Mandatory evaluation card for every recommended idea

Complete **every** field. If any of the first four cannot be answered concretely, **do not recommend the idea**.

| Required field | What must be stated |
| --- | --- |
| Cost to remove (C) | Exact resource and the proposed intervention/approximation |
| Critical computation/representation (I) | Internal mechanism being tested and why it might matter |
| Capability to retain (P) | Specific capability, metric, and acceptable degradation |
| Falsification test (T) | Intervention, controls, fixed-cost baselines, and measurable outcomes |
| Relationship to the theme | One direct causal sentence; not "it uses diffusion/vision/ML" |
| Closest prior work | Named papers, overlapping claims, and credible novelty gap |
| Evidence level | Hypothesis / validated pilot / independently reproduced / mature |
| Existing project evidence | Relevant code and results **including failures**, with links |
| Feasibility and risk | Data, model, GPU needs, schedule, blockers, confounds |
| Go/no-go | Exact experiment and reason to abandon, revise, or continue |

## 5. Response and honesty rules

- State **"fails the hard rule"** when C/I/P/T is missing. No post-hoc thematic rationalization.
- Distinguish **theme fit**, **novelty**, **experimental feasibility**, and **conference readiness** as separate judgments.
- Never infer that preserving task success proves the preservation of a particular internal representation. Require mechanism-specific ablations or interventions.
- Never infer practical efficiency solely from model evaluations, FLOPs, or parameter counts when deployment latency/energy/memory is the claim.
- Never hide negative GitHub results or replace them with earlier more favorable results.
- Give the user the best evidence-supported recommendation, which can be **"none of the current candidates qualifies."**
- If the user's request calls for fresh prior-art or deadline checking, verify current sources. If verification is unavailable, state that clearly.

## 6. Enforcement scope

This policy is a durable, repository-readable decision standard. It guides assistants and collaborators who **read the repository instructions**; the presence of these files cannot guarantee that every external AI assistant or future chat will load and obey them. For a new assistant session, explicitly provide this policy or request that it read the repository instructions before brainstorming.
