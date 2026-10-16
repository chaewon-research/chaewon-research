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

**AladdinAI** — Contributed upstream improvements to native C/Python infrastructure, including robust DOCX parsing and session-isolated dataset splitting for AI evaluation.

[DOCX Parsing](https://github.com/aliyevaladddin/AladdinAI/pull/972) · [Dataset Splitting](https://github.com/aliyevaladddin/AladdinAI/pull/929)

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
