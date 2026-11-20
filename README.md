# Chaewon Yoon

**Efficient and Reliable Machine Learning**  
Data Science, University of Wisconsin-Madison

I study how to make machine-learning systems more efficient without losing the computations and representations that matter for their behavior. My work spans numerical precision, inverse vision, neural operators, and mechanistic interpretability. I also contribute to diffusion-based reconstruction research in Professor Grigoris Chrysos's group at UW-Madison.

[**Research Résumé**](Chaewon_Yoon_Resume.pdf) · [**Academic CV**](Chaewon_Yoon_CV.pdf) · [LinkedIn](https://www.linkedin.com/in/chaewon-yoon-542a14328) · [Hugging Face](https://huggingface.co/melover24) · [Email](mailto:chaewon.yoon.ds@gmail.com)

## Research Direction

> Which computations can we approximate or remove without changing the capabilities we need to preserve?

I investigate precision-sensitive operations, model internals, and evaluation methods that reveal when efficiency gains come at a meaningful cost to reliability.

## Publications

**The Measurement Operator Changes Which Bits Matter: Operator-Conditioned Mixed Precision for Inverse Vision**  
*IEEE/CVF Winter Conference on Applications of Computer Vision (WACV 2027), Algorithms Track. Accepted.*

Introduces Operator-Susceptibility Matching (OSM), which uses information about the sensing operator to select mixed-precision schedules. In a controlled eight-stage study, OSM reduced mean normalized operator-visible regret to **2.7%**, compared with **6.3%** for the best global-static schedule at the same three-stage high-precision budget. A separate native A100 timing experiment recorded **16.4 ms** per reconstruction versus **23.6 ms** for its FP16 reference (**1.44×** speedup). The quality and timing results use distinct evaluation protocols.

[Paper](https://github.com/chaewon-research/operator-conditioned-mixed-precision/blob/main/Yoon_WACV2027_Operator_Conditioned_Mixed_Precision_Author_Manuscript.pdf) · [Research repository](https://github.com/chaewon-research/operator-conditioned-mixed-precision)

**EvidenceLens: A Declarative Evidence-State Interface for Human-AI Visual Inspection**  
*ACM UIST Adjunct 2026, poster publication.*

A declarative evidence-state interface for bounded human-AI visual inspection and review.

[Publication DOI](https://doi.org/10.1145/3830397.3841901) · [Paper](https://github.com/chaewon-research/evidencelens/blob/main/paper/EvidenceLens_UIST_Adjunct_2026.pdf) · [Repository](https://github.com/chaewon-research/evidencelens)

## Selected Research

**Quantized Defect Correction for Fractional Neural Operators**  
Investigates precision-sensitive failures in fractional-PDE neural operators through activation and weight quantization, physics-residual diagnostics, and selective defect correction with numerical and hardware evaluations.

[Preprint](https://github.com/chaewon-research/qdc-fractional-neural-operators/blob/main/paper/QDC_Fractional_Neural_Operators_Preprint_2026.pdf) · [Code and reproduction](https://github.com/chaewon-research/qdc-fractional-neural-operators) · [Software DOI](https://doi.org/10.5281/zenodo.21977847)

**EvAudit: Latent Proxy-Evidence Auditing for Generative Data Mining**  
Developed an evidence-auditing framework to filter unsupported claims before downstream use. The public research artifact includes calibration and stability checks, validation utilities, reproducibility scripts, and a 2026 preprint.

[Preprint and research artifact](https://github.com/chaewon-research/evaudit) · [Software DOI](https://doi.org/10.5281/zenodo.22026272)

**Multilingual LLM Mechanistic Interpretability**  
Contributed to Qwen and Llama circuit-discovery studies using activation patching, attention-path interventions, and held-out controls. Additional experiments examine whether language-control mechanisms transfer across model variants.

[Qwen circuit study](https://github.com/arjunpil/circuit-targeted-language-intervention-multilingual-llm/pull/3) · [Llama validation](https://github.com/arjunpil/circuit-targeted-language-intervention-multilingual-llm/pull/8) · [Cross-model analysis](https://github.com/arjunpil/LIHA-First-Token-Broadcasters/pull/12)

## Selected Open-Source Research Contributions

- **Station House, LLM Consciousness Self-Attribution:** Developed OLMo 3 identity-spoofing elicitation pilots across SFT, DPO, and Instruct, covering 81 recorded conversations across three training stages. Contributed evaluation tooling and grading-context analysis. [Initial pilot](https://github.com/Station-House/LLMConsciousnessSelfAttributionRepo/pull/7) · [Training-stage extension](https://github.com/Station-House/LLMConsciousnessSelfAttributionRepo/pull/14) · [Evaluation tooling](https://github.com/Station-House/LLMConsciousnessSelfAttributionRepo/pull/16)

- **Station House, Marin Neuron Hunt:** Investigated Marin 32B neuron behavior using activation examples and targeted contrast experiments. Developed and revised neuron explanations through negative-side tests, numeric-context sensitivity checks, and follow-up experiments that refuted earlier hypotheses. Multiple contributions were merged. [Initial explanations](https://github.com/Station-House/marin-neuron-hunt/pull/19) · [Verification experiments](https://github.com/Station-House/marin-neuron-hunt/pull/55) · [Numeric-context tests](https://github.com/Station-House/marin-neuron-hunt/pull/84) · [Revised explanation](https://github.com/Station-House/marin-neuron-hunt/pull/90)

- **Station House, ConspiracyBench:** Contributed a merged, evidence-backed benchmark question and examined benchmark design, duplicate detection, evidence-focused evaluation, and paraphrase robustness. [Merged benchmark contribution](https://huggingface.co/spaces/Station-house/ConspiracyBench/discussions/77) · [Evaluation proposal](https://huggingface.co/spaces/Station-house/ConspiracyBench/discussions/441)

- **Medical-Imaging Robustness Study:** Contributed merged model-training, inference, and evaluation infrastructure, including dataset validation, baseline setup, prediction exports, and an ImageNet-pretrained baseline. [Dataset and training setup](https://github.com/SamsondareHUB/mammography-robustness-study/pull/3) · [Prediction exports](https://github.com/SamsondareHUB/mammography-robustness-study/pull/8) · [Baseline implementation](https://github.com/SamsondareHUB/mammography-robustness-study/pull/10)

- **StellarResearch, AdaptiveRL:** Added a merged LiDAR noise and dropout robustness benchmark for an adaptive reinforcement-learning project. [Robustness benchmark](https://github.com/StellarResearch/ARL/pull/306)

- **AladdinAI:** Contributed merged session-aware dataset splitting and DOCX parsing fixes. The inline-image ordering fix was recognized by the XERJ Corpus Hub. [Dataset splitting](https://github.com/aliyevaladddin/AladdinAI/pull/929) · [DOCX fix](https://github.com/aliyevaladddin/AladdinAI/pull/974) · [Contributor page](https://hub.xerj.org/contributors/chaewon-research)

- **CausationEntropy:** Contributed conditional mutual information estimator fixes and Gaussian CMI performance optimization. [CMI fix](https://github.com/Center-For-Complex-Systems-Science/causationentropy/pull/48) · [Optimization](https://github.com/Center-For-Complex-Systems-Science/causationentropy/pull/43)

## Selected Presentations

- **UW-Madison Sustainability Symposium 2026:** *When Does Better AI Actually Save More Energy? Decision-Aware Adaptive Fidelity for Building Control.* [Poster](https://github.com/chaewon-research/research-posters/blob/main/Yoon_2026_UW_Madison_Sustainability_Symposium_Poster.pdf) · [DOI](https://doi.org/10.5281/zenodo.23750255)
- **WiSys SPARK Symposium 2026:** *Placement-Aware Quantization for Fractional-PDE Neural Surrogates.* [DOI](https://doi.org/10.5281/zenodo.22044287)
- **Pi Mu Epsilon Regional Undergraduate Mathematics Conference 2025:** *Numerical Stability and Convergence of Physics-Constrained Neural Networks in Vibration Modeling.* [DOI](https://doi.org/10.5281/zenodo.22044564)

## Selected Honors & Awards

- **Judge's Choice Award, Most Innovative Track (2026):** UW-Madison Tech Exploration Lab Demo Night, [PawSight](https://github.com/chaewon-research/PawSight).
- **1st Place, Culver's Business Model Competition (2025):** UW Oshkosh, [CurbMap 360](https://github.com/chaewon-research/curbmap-360). [University feature](https://www.uwosh.edu/today/126855/uwo-student-entrepreneurs-ai-powered-map-for-people-with-mobility-challenges-tops-culver-pitch-contest/).
- **Calculus Prize Exam Winner (2025):** $1,000 mathematics scholarship.

More experimental work, preprints, and software are available in my [research repositories](https://github.com/chaewon-research?tab=repositories).