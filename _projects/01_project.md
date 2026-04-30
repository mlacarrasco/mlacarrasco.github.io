---
layout: page
title: Multiple View Visual Inspection of Glass Bottlenecks
description: Automated visual inspection system for wine glass bottles using uncalibrated multiple-view analysis (2006-2010).
img: assets/img/portafolio_proyectos_1.jpg
importance: 4
category: research
related_publications: true
---

**CONICYT ACT-32 — Pontificia Universidad Católica de Chile (2006–2010)**  
**Role:** Researcher & Developer

---

##### Overview

Glass bottleneck inspection is a critical yet underexplored problem in automated quality control. Even a flaw of only 1–2 mg in every 100 mg article can be enough to trigger 100% rejection rates — and undetected flaws near the bottleneck pose direct risks to consumers, for example when cork insertion detaches glass particles from a defective region.

This project developed a machine vision system for the automated inspection of empty wine glass bottles, focusing specifically on the **bottleneck** — the most structurally challenging region due to its narrow geometry and susceptibility to false alarms. The system operates on **uncalibrated image sequences**, requiring no camera calibration, which makes it practical for real industrial environments.

---

##### Electro-Mechanical Acquisition System

A custom electro-mechanical prototype was designed and built to capture multiple views of the bottleneck using a **single CCD camera** (Canon S3 IS, 2592×1944 px). The bottle and an internal illumination tube rotate simultaneously at configurable angles, controlled by a stepper motor and a Basic Stamp PIC16C57 microcontroller via RS232.

A key innovation of the prototype is the **internal illumination system**: a tube inserted inside the bottle with four LEDs emitting uniform white light and a reflecting layer at the opposite end. This avoids the intrinsic reflections produced by external light sources and greatly improves image definition, increasing the probability of capturing even the smallest flaws.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/video_prototipo_maquina.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_1.jpg" title="Electro-mechanical inspection prototype" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Prototype in operation. Right: Detail of the acquisition setup showing the internal illumination tube and control markers used for geometric correspondence across views.
</div>

---

##### Inspection Methodology: AMVI

The system is based on the **Automated Multiple View Inspection (AMVI)** paradigm: rather than deciding from a single image whether a candidate region is a real flaw or a false alarm, the system tracks candidate regions across multiple views. The key insight is that **only real flaws induce consistent geometric and featural relations across views**, while noise and false alarms appear as random events.

The pipeline consists of three stages:

###### 1. Segmentation & Feature Extraction
Each image is processed by two Gaussian filters: a noise-removal (NR) filter and a structure-removal (SR) filter. Their absolute difference is binarized to extract candidate regions. Each region is described by a rich set of feature descriptors including HU moments, co-occurrence matrices, SIFT, SURF, PHOG, and several affine/photometric invariants (FSK, FSKS, PSO*, GPSO, GPD, CLP).

###### 2. Corresponding Points Between Views
Equidistant **control markers** placed on both ends of the illumination tube serve as reliable anchor points. Their known relative positions across views enable computation of the fundamental matrices and trifocal tensors needed for geometric analysis — without any camera calibration.

###### 3. Tracking Flaws in Multiple Views
Flaw candidates are tracked using **bifocal** (two-view) and **trifocal** (three-view) geometric constraints. To resolve ambiguous many-to-many geometric matches, a novel **bidirectional Nearest Neighbour Distance Ratio (bNNDR)** criterion was introduced. Unlike the standard NNDR, bNNDR checks matches in both directions between views, weighting ambiguous correspondences to suppress false positives while preserving true detections.

---

##### Results

The system was evaluated on 120 color image sequences of wine bottle bottlenecks, each consisting of 3 views separated by 15° rotation. Flaws ranged from 0 to 4 per image (avg. 2.8), and false alarms from 0 to 10 (avg. 9.5). The smallest detected flaw covered approximately 9 pixels, equivalent to 0.16 mm² on the bottle surface.

| Configuration | True Positive Rate | False Positive Rate |
|---|---|---|
| 2 Views (geometry only) | 99.9% | 46.4% |
| 2 Views + bNNDR | 99.9% | 30.2% |
| 3 Views (geometry only) | 99.1% | 2.5% |
| **3 Views + bNNDR** | **99.1%** | **0.9%** |

The three-view inspection with bNNDR achieves the best trade-off, with a **99.1% true positive rate** and a **0.9% false positive rate** — the most accurate results reported in literature for glass bottleneck inspection at the time of publication. Total processing time for three views averaged **1.3 seconds** in MATLAB on a Pentium Centrino 2.0 GHz.

---

##### Funding & Acknowledgements

This project was partially supported by **CONICYT** (grant no. 21050185) and the School of Engineering at Pontificia Universidad Católica de Chile.

---

Cite: {% cite carrasco2010visual %}.