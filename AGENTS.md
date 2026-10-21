# Instructions for Research-Recommendation Assistants

**Before proposing or ranking any research idea based on this repository**, read the canonical **Research Direction** in [README.md](README.md) and the full [Research Recommendation Policy](RESEARCH_RECOMMENDATION_POLICY.md).

The user's hard rule is not merely "related to efficient ML." A proposed idea qualifies only if it explicitly:
1. Reduces a concrete computational cost.
2. Identifies internal computations **or** representations that might be indispensable.
3. Preserves a specific model capability under that reduction.
4. Includes a falsifiable intervention and a cost-matched comparison that test that connection.

**Fail closed.** If any condition is missing, do not recommend the idea. Do not select a convenient existing project first and retrofit an explanation of alignment afterward. Do not assume inverse vision, geometric solvers, diffusion, or quantization are preferred. Research across the full stated theme.

Keep theme eligibility separate from novelty, prior-art overlap, evidence quality, implementation readiness, and conference fit. Read latest experiment logs and negative results before claiming an existing project is feasible. Cite relevant repositories and external papers where available; do not invent baselines or results. Propose quantitative, testable next steps and an explicit stop rule.

For each recommendation use the policy's **mandatory evaluation card**. If no candidate meets the gate, say so rather than giving a weak recommendation.

These files govern repository-informed recommendations for agents that read them; they do not override a user's later explicit instructions.
