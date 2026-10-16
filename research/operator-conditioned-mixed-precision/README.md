# The Measurement Operator Changes Which Bits Matter: Operator-Conditioned Mixed Precision for Inverse Vision

**Chaewon Yoon**

**Accepted to the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV 2027), Algorithms Track.** Proceedings forthcoming.

## Overview

The precision requirements of an inverse-vision model depend not only on its network architecture but also on the sensing operator used to acquire its measurements. This work studies how changes in sensing geometry alter the stages most sensitive to reduced numerical precision.

We introduce **Operator-Susceptibility Matching (OSM)**, which uses a calibrated measurement operator to rank stage-level precision sensitivity and select a mixed-precision schedule without exhaustive schedule search for each new operator.

## Results

In controlled experiments with an eight-stage reconstruction model, changing sensing geometry altered the ordering of precision-sensitive stages. At the primary three-stage precision budget, OSM achieved **2.7% mean normalized operator-visible regret**, compared with **6.3%** for the best global-static schedule.

A separate native A100 benchmark measured **16.4 ms** for the selected mixed-precision configuration and **23.6 ms** for the FP16 reference, corresponding to a **1.44×** latency speedup. Reconstruction-quality and native-execution measurements use separate evaluation protocols.

## Research areas

Computational imaging · Inverse problems · Mixed-precision inference · Quantization · Efficient machine learning

## Citation

Chaewon Yoon. *The Measurement Operator Changes Which Bits Matter: Operator-Conditioned Mixed Precision for Inverse Vision.* Accepted to the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV), 2027. Proceedings forthcoming.
