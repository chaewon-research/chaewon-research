# Chaewon Yoon

**Efficient and Reliable Machine Learning**  
Data Science, University of Wisconsin-Madison

I study how to reduce the computational cost of machine-learning systems while preserving the internal computations and representations that support their capabilities. My work spans numerical precision, inverse vision, neural operators, and mechanistic interpretability. I am also involved in diffusion-based reconstruction research in Professor Grigoris Chrysos's group at UW-Madison.

[**Research Résumé**](Chaewon_Yoon_Resume.pdf) · [**Academic CV**](Chaewon_Yoon_CV.pdf) · [LinkedIn](https://www.linkedin.com/in/chaewon-yoon-542a14328) · [Hugging Face](https://huggingface.co/melover24) · [Email](mailto:chaewon.yoon.ds@gmail.com)

## Research Direction

> How far can we reduce the computational cost of machine-learning systems without losing the internal computations or representations that are important for their capabilities?

My current focus is on identifying which computations are sensitive to approximation, explaining why they matter, and testing when targeted precision or computation can preserve model behavior at lower cost.

## Publications

**The Measurement Operator Changes Which Bits Matter: Operator-Conditioned Mixed Precision for Inverse Vision**  
*IEEE/CVF Winter Conference on Applications of Computer Vision (WACV 2027), Algorithms Track. Accepted.*

Introduces Operator-Susceptibility Matching (OSM) to select mixed-precision schedules using information about the sensing operator. In a controlled eight-stage study, OSM reduced mean normalized operator-visible regret to **2.7%**, compared with **6.3%** for the best global-static schedule at the same three-stage high-precision budget. A separate native A100 timing experiment recorded **16.4 ms** per reconstruction versus **23.6 ms** for its FP16 reference (**1.44×** speedup). The quality and timing results use distinct evaluation protocols.

[Paper](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/Yoon_WACV2027_Operator_Conditioned_Mixed_Precision_Author_Manuscript.pdf) · [Research repository](https://github.com/chaewon-research/operator-conditioned-mixed-precision)

**EvidenceLens: A Declarative Evidence-State Interface for Human-AI Visual Inspection**  
*ACM UIST Adjunct 2026, poster publication.*

A declarative evidence-state interface for bounded human-AI visual inspection and review.

[Publication DOI](https://doi.org/10.1145/3830397.3841901) · [Paper](https://github.com/chaewon-research/evidencelens/blob/main/paper/EvidenceLens_UIST_Adjunct_2026.pdf) · [Repository](https://github.com/chaewon-research/evidencelens)

## Selected Research

**Quantized Defect Correction for Fractional Neural Operators**  
Research on precision-sensitive failures in fractional-PDE neural operators. Investigates activation and weight quantization, physics-residual diagnostics, and selective defect correction with controlled numerical and hardware evaluations.

[Preprint](https://github.com/chaewon-research/qdc-fractional-neural-operators/blob/main/paper/QDC_Fractional_Neural_Operators_Preprint_2026.pdf) · [Code and reproduction](https://github.com/chaewon-research/qdc-fractional-neural-operators) · [Software DOI](https://doi.org/10.5281/zenodo.21977847)

**Multilingual LLM Mechanistic Interpretability**  
Contributed to Qwen and Llama circuit-discovery studies using exact activation patching, source-to-destination interventions, and held-out, layer-matched controls. Additional work explores language-retention mechanisms across model families.

[Qwen circuit study](https://github.com/arjunpil/circuit-targeted-language-intervention-multilingual-llm/pull/3) · [Llama validation](https://github.com/arjunpil/circuit-targeted-language-intervention-multilingual-llm/pull/8) · [Cross-model analysis](https://github.com/arjunpil/LIHA-First-Token-Broadcasters/pull/12)

## Selected Open-Source Contributions

- **Station House:** Developed and merged an OLMo 3 identity-spoofing pilot with nine conditions, 27 recorded conversations, and three scoring approaches. [Merged research contribution](https://github.com/Station-House/LLMConsciousnessSelfAttributionRepo/pull/7)
- **AladdinAI:** Contributed merged session-aware dataset splitting, DOCX parsing fixes, and evaluation software improvements. The inline-image ordering fix was recognized by the XERJ Corpus Hub. [Dataset splitting](https://github.com/aliyevaladddin/AladdinAI/pull/929) · [DOCX fix](https://github.com/aliyevaladddin/AladdinAI/pull/974) · [Contributor page](https://hub.xerj.org/contributors/chaewon-research)
- **CausationEntropy:** Contributed causal-discovery tests and conditional mutual information estimator fixes. [Merged CMI fix](https://github.com/Center-For-Complex-Systems-Science/causationentropy/pull/48)

## Selected Presentations

- **WiSys SPARK Symposium 2026:** *Placement-Aware Quantization for Fractional-PDE Neural Surrogates.* [DOI](https://doi.org/10.5281/zenodo.22044287)
- **Pi Mu Epsilon Regional Undergraduate Mathematics Conference 2025:** *Numerical Stability and Convergence of Physics-Constrained Neural Networks in Vibration Modeling.* [DOI](https://doi.org/10.5281/zenodo.22044564)

Additional manuscripts, experimental artifacts, and software are available in my [research repositories](https://github.com/chaewon-research?tab=repositories).
