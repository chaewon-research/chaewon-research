# Research Recommendation Policy

**Source of authority:** the user's hard rule is to recommend ideas only when they *directly align with their big research theme, explicitly stated in GitHub*. The theme is copied verbatim below. All other procedures in this file are proposed **operational checks**, not additional user-stated rules.

## The one hard rule

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

**The rule decides candidate eligibility BEFORE convenience, familiarity, CVPR deadlines, or rankings.** Alignment must be the *scientific question*, not a post-hoc paragraph about related topics.

## Mandatory theme-alignment decision

For **each** candidate, complete the following four-part causal sentence:

> We will reduce **[specific computational resource]** by approximating/removing **[named internal computation or representation]**, while preserving **[specific capability]**; **[intervention/controlled test]** will distinguish critical from expendable computation at matched cost.

Evaluate these as diagnostic questions derived from the user's theme:

| Diagnostic | What must be explicit | Reject when |
| --- | --- | --- |
| **C: Cost reduced** | Where computation is removed; which resource and measurement (latency/energy/memory/bandwidth/model calls) | Merely improves image quality or task score with no computational reduction |
| **I: Internal mechanism** | Which model computation/representation is potentially capability-critical; what perturbation targets it | Only calls something "important" without identifying what is preserved |
| **P: Preserved capability** | Capability-level performance to preserve and relevant degradation measure | Only generic visual appeal or irrelevant proxy scores |
| **T: Test** | Proposed intervention/ablation and cost-matched comparator to examine whether I causes P's deterioration under C | Unfalsifiable claim or no means of separating mechanism from generic compute reduction |

**Conceptual PASS:** all four are specifically and falsifiably proposed, even if experiments have not yet been run. Label these ideas **THEME-ALIGNED / UNVALIDATED** until tested.  
**FAIL:** any of C/I/P/T is absent or vague, or the actual scientific question is not about the cost–critical-internals–capability relationship. Do not recommend it; explain the gap.  
**INDETERMINATE:** current candidate description or evidence is insufficient; refine and rerun the gate before recommending.

The actual user rule is the quoted research question; C/I/P/T are the assistant's *transparent test for it*. Do **not** assert that the user independently demanded a certain method or a specific experimental protocol.

## Selection and ranking workflow

1. **Read fresh sources:** [README.md](README.md), this policy, [AGENTS.md](AGENTS.md), current relevant experiment logs/READMEs, and [retrospective audit](RECOMMENDATION_AUDIT.md) before a new recommendation.
2. **Generate varied candidates before choosing a favorite.** Search across precision/compression, adaptive execution, visual perception/reasoning, representation preservation, systems, and architectures where appropriate. No mandatory preference for diffusion, inverse vision, geometric solvers, or extensions of accepted papers.
3. **Gate every candidate independently:** write the actual C/I/P/T answers; discard FAIL and INDETERMINATE from rankings. Do not choose a topic first then append an "alignment" rationale.
4. **Only for passes, evaluate separate dimensions:** (a) closest prior art and credible scientific novelty; (b) state of evidence and negative results; (c) cost-measurement validity and feasibility; (d) conference scope and timing; (e) differentiation from accepted work.
5. **Document evidence rather than invent it:** distinguish *hypothesis*, *documented pilot*, and *reproduced experiment*; identify unmatched protocols, missing data, and adverse results.
6. **Recommend only from eligible, evidence-supported candidates**, with a comparison against alternatives and one falsification experiment. If all eligible ideas have prohibitive novelty/evidence/feasibility problems, state **NO CURRENT VIABLE RECOMMENDATION**. A deadline never overrides the theme rule.

## Required decision record for a proposed recommendation

```markdown
### Candidate: [actual scientific idea; not just a fashionable topic]
Theme statement (one causal sentence): Reduce [C] by altering [I] while protecting [P], tested through [T].
Cost reduced (C): [resource, intervention, and proposed metric]
Internal computation/representation (I): [specific mechanism + perturbation]
Capability preserved (P): [named capability, measurement + loss tolerance]
Counterfactual verification (T): [controlled comparison, matched budget + actual runtime]
Theme verdict: PASS / FAIL / INDETERMINATE
Evidence: HYPOTHESIS / PILOT / REPRODUCED (with links; include negative results)
Closest prior art and novelty gap: [named references with dates and honest unknowns]
Relation to existing accepted work: [what is actually new vs WACV or other paper]
Feasibility: [model, data, compute, timeline, blockers]
Conference readiness: NOT READY / PROMISING / SUBMISSION-SUPPORTED
Go/no-go test: [specific result that changes the decision]
Final action: RECOMMEND / REVISE / REJECT / DEFER, with reason
```

A **PASS** does not imply novelty, publishability, real runtime improvement, or CVPR acceptance. Only label **RECOMMEND** when those separate constraints have been assessed sufficiently to support the user's actual request.

## Evidence hygiene

- Measure real hardware runtime/energy if claiming practical acceleration; separate it from FLOPs, denoiser-step counts, and inference under different protocols.
- Distinguish **capability preservation** from mere output similarity, and correlate internal interventions with the claimed capability.
- Include the strongest relevant positive and negative experiments; don't suppress failures.
- Recheck recent primary papers and official conference instructions when timing/novelty matters; explicitly state if not verified.
- Report known overlapping methods; never claim global novelty from a brief search.
- Never infer that an untested plan already preserves a representation or reduces cost.
- If the assistant has not completed the decision record, it must not call that idea its "best recommendation."

## Scope and auditing

[RECOMMENDATION_AUDIT.md](RECOMMENDATION_AUDIT.md) explicitly applies the rule to previous suggestions and records **no currently cleared best CVPR proposal**. Future recommendations should append a dated decision record before calling a candidate "recommended." Evidence changes should update the record rather than silently replacing negative results.

This file is a repository-readable standard for agents and humans who encounter it. GitHub text cannot technically force an unrelated chat or external agent to obey it; a new agent must read the guidance. The file is not a substitute for substantive scientific evaluation.
