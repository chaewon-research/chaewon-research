# Research Recommendations: Read and Enforce Before Proposing

This repository's source of truth is the exact **Research Direction** in [README.md](README.md):

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

**User's hard rule:** only recommend a research idea that directly addresses that overarching question. Do not replace the user's rule with your own convenient specialty or scoring rubric.

**Mandatory workflow before producing a recommendation:**

1. Read [RESEARCH_RECOMMENDATION_POLICY.md](RESEARCH_RECOMMENDATION_POLICY.md) and [RECOMMENDATION_AUDIT.md](RECOMMENDATION_AUDIT.md), along with current relevant GitHub project files.
2. Generate candidates across the *full theme* rather than defaulting to the existing WACV paper, geometric-solver experiments, inverse vision, diffusion, or quantization.
3. For **every candidate** complete the policy's C/I/P/T causal sentence: cost removed, critical internal computation or representation, capability preserved, and decisive test. The four checks are a *way to operationalize* the user's one hard rule, not a replacement for it.
4. **Fail closed:** don't rank, propose as "best," or recommend candidates with absent/vague C/I/P/T answers. Separate **THEME PASS** from **EMPIRICALLY VALIDATED** and **CVPR READY**.
5. For passes only, examine current primary prior work, existing accepted papers, current project evidence including negative results, actual compute measurements, and feasible validation. Don't equate familiar repositories or speculative hypotheses with scientific strength.
6. Fill the policy's **required decision record** in the response (and update the audit if asked to save the decision). If none is evidence-supported, say **no current viable recommendation**.

**Previously suggested ideas are NOT cleared as top CVPR proposals.** See the audited verdicts; the geometric-solver repo documents significant negative generation results.

This is guidance for assistants who read this repository, not a guarantee that every other model/session will load it.
