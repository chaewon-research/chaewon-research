# Chaewon Yoon

Data Science · University of Wisconsin–Madison

My research focuses on **efficient and reliable machine learning**, particularly the effects of reduced numerical precision and computational constraints on model behavior. I study how to identify the computations most sensitive to approximation and preserve them without sacrificing the efficiency gained elsewhere.

I am also part of Professor Grigoris Chrysos's research group at UW–Madison, exploring diffusion-based reconstruction.

**Research interests:** Efficient Machine Learning · Quantization · Model Compression · Adaptive Computation · Neural Operators · ML Systems

[CV](https://github.com/chaewon-research/chaewon-research/blob/main/Chaewon_Yoon_CV.pdf) · [LinkedIn](https://www.linkedin.com/in/chaewon-yoon-542a14328) · [Email](mailto:chaewon.yoon.ds@gmail.com)

---

## Research Direction

My research is guided by a central question:

**How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?**

I approach this question through numerical precision, selective computation, and the structure of approximation errors. My current research examines these problems in neural operators and inverse-vision models, with broader interests in efficient inference, representation compression, and larger neural architectures.

### Hard Rule for Research Idea Recommendations

A recommended research idea **must directly investigate reducing the computational cost of an ML system while identifying and preserving specific internal computations or representations that are important to a defined capability**. The idea must say **what computation will be reduced, what critical internal mechanism may be lost, which capability must survive, and how both the cost savings and preservation claim will be tested**. Otherwise, **reject it**—even if the topic is fashionable, feasible, vision-related, or similar to past projects.

This rule is **architecture- and application-agnostic**: do not default to inverse vision, diffusion, quantization, geometric solvers, or extensions of existing papers merely because they are familiar. Matching the theme is a necessary gate, **not** proof of novelty, soundness, conference fit, or readiness.

See the [Research Recommendation Policy](RESEARCH_RECOMMENDATION_POLICY.md) for the mandatory eligibility test, evidence requirements, and evaluation template. Assistants should also follow [AGENTS.md](AGENTS.md).

---

## Publications and Accepted Papers

### WACV 2027

**The Measurement Operator Changes Which Bits Matter: Operator-Conditioned Mixed Precision for Inverse Vision**

*IEEE/CVF Winter Conference on Applications of Computer Vision (WACV 2027), Algorithms Track. Accepted.*

This paper studies how the sensing operator influences precision sensitivity in inverse-vision reconstruction. It introduces **Operator-Susceptibility Matching (OSM)**, which uses calibrated operator information to select mixed-precision schedules without exhaustive per-operator search.

[Research Repository](https://github.com/chaewon-research/operator-conditioned-mixed-precision)

*Proceedings forthcoming.*

### ACM UIST Adjunct 2026

**EvidenceLens**

*ACM Symposium on User Interface Software and Technology (UIST Adjunct 2026), Poster Publication.*

Evidence-state interfaces for bounded human-AI visual inspection.

[Repository](https://github.com/chaewon-research/evidencelens) · [Paper](https://github.com/chaewon-research/evidencelens/blob/main/paper/EvidenceLens_UIST_Adjunct_2026.pdf) · [ACM DOI](https://doi.org/10.1145/3830397.3841901)

---

## Ongoing Research

### Quantized Defect Correction (QDC)

**Conditional Precision Bottlenecks and Quantized Defect Correction in Fractional Neural Operators**

QDC investigates how quantization affects different components of neural operators and whether numerical defects can be corrected selectively under fixed computational budgets.

The project studies weight and activation sensitivity, physics-based residual diagnostics, and selective precision correction. Its evaluations include fractional-PDE neural operators and GPU inference under low-precision arithmetic.

[Repository](https://github.com/chaewon-research/qdc-fractional-neural-operators) · [Preprint](https://github.com/chaewon-research/qdc-fractional-neural-operators/blob/main/paper/QDC_Fractional_Neural_Operators_Preprint_2026.pdf) · [Software DOI](https://doi.org/10.5281/zenodo.21977847)

### CausationEntropy

Collaborative research on causal discovery and conditional mutual information estimation, with emphasis on statistical validity and computational efficiency.

[Research Repository](https://github.com/Center-For-Complex-Systems-Science/causationentropy)

---

## Selected Open-Source Contributions

**Station House** — Developed an OLMo 3 identity-spoofing research pilot, reproducible LLM evaluation tooling, and contributed to benchmark review.

[Research Contribution](https://github.com/Station-House/LLMConsciousnessSelfAttributionRepo/pull/7) · [Hugging Face](https://huggingface.co/spaces/Station-house/ConspiracyBench)

**AladdinAI** — Contributed merged C/Python fixes for DOCX table parsing and inline image ordering, alongside session-isolated, versioned dataset splitting for AI evaluation. The inline-image fix was selected for the [XERJ Corpus Hub](https://hub.xerj.org/contributors/chaewon-research) as a reference implementation for AI coding agents.

[DOCX Table Parsing](https://github.com/aliyevaladddin/AladdinAI/pull/972) · [Inline Image Ordering](https://github.com/aliyevaladddin/AladdinAI/pull/974) · [Dataset Splitting](https://github.com/aliyevaladddin/AladdinAI/pull/929)  
[![XERJ Corpus Hub contributor](https://hub.xerj.org/contributors/chaewon-research/badge.svg)](https://hub.xerj.org/contributors/chaewon-research)

---

## Other Research

### C-TEA

Risk-aware active evidence acquisition under workflow, resource, safety, and review-capacity constraints.

[Repository](https://github.com/chaewon-research/c-tea) · [Preprint](https://github.com/chaewon-research/c-tea/blob/main/paper/C_TEA_Constrained_Template_Evidence_Acquisition_Preprint_2026.pdf)

### Transition-Preserving State Tracking

Controlled generation and auditable state tracking for multi-turn structured interfaces.

[Repository](https://github.com/chaewon-research/transition-preserving-state-tracking) · [Preprint](https://github.com/chaewon-research/transition-preserving-state-tracking/blob/main/paper/Transition_Preserving_State_Tracking_DGTC_Preprint_2026.pdf)

Additional projects are available in my [GitHub repositories](https://github.com/chaewon-research?tab=repositories).

---

## Selected Presentations

**WiSys SPARK Symposium 2026**  
*Placement-Aware Quantization for Fractional-PDE Neural Surrogates*  
[DOI](https://doi.org/10.5281/zenodo.22044287)

**Pi Mu Epsilon Regional Undergraduate Mathematics Conference 2025**  
*Numerical Stability and Convergence of Physics-Constrained Neural Networks in Vibration Modeling*  
[DOI](https://doi.org/10.5281/zenodo.22044564)
