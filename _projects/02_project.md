---
layout: page
title: Reach-to-Grasp Movement Detection via Eye–Hand Coordination
description: A multimodal computer vision system that fuses eye-tracker and wrist-mounted camera data to detect and predict grasping movements using Hidden Markov Models — without markers on objects (2011–2013).
img: assets/img/portafolio_proyectos_2.jpg
importance: 3
category: research
related_publications: true
---

**Funding:** FONDECYT-CONICYT Initiation into Research — Grant no. 11100098 (2011–2013)  
**Role:** Principal Researcher

---

#### Motivation

Human beings effortlessly reach for and grasp objects under a wide variety of conditions — different positions, orientations, shapes and lighting. This natural ability, governed by the brain's **eye–hand coordination** system, is poorly understood and difficult to replicate computationally. Understanding it matters not only scientifically, but also practically: people suffering from neurodegenerative diseases (causing tremor, slowness, or imprecision) depend on intact eye–hand coordination to perform basic daily tasks like grasping objects. When that coordination breaks down, a system capable of predicting grasping intent could enable assistive devices or rehabilitation robots to compensate.

Despite extensive work on sign language and communicative gesture recognition, **grasping movements** — actions directed at the physical environment — had received comparatively little attention in computer vision.

---

#### Approach

This project proposes a novel multimodal system that fuses **two wearable viewpoints** to detect and predict reach-to-grasp actions:

- **Eye-tracker** (ASL Eye-Trac 6): captures the user's field-of-view and estimates gaze position in real time
- **Wrist-mounted micro-camera**: captures what the hand approaches during a grasping action

Rather than observing the user from a fixed external camera, the system exploits **the user's own perspective** — the same visual information available to the brain during a grasping task.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/paper_MVA.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_2.jpg" title="Dual-viewpoint acquisition setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Temporal Slide Window (TSW) motion detection in action. Right: Dual-camera acquisition setup — eye-tracker (head) and micro-camera (wrist).
</div>

---

#### Methodology

The pipeline has two coupled stages.

##### Stage 1 — Hand Motion Recognition (wrist camera)

A **Temporal Slide Window (TSW)** approach processes video sequences captured by the wrist camera. For each window, SURF interest points are matched across non-consecutive frames (spaced δ frames apart), and a set of **eight motion indicators** is extracted:

- **Grasp motion** (reach vs. retreat) — via convergence of motion vectors toward an intersection point
- **Rotational motion** — angular velocity across corresponding points
- **Rotational area** and **rotational normal area** — geometric area swept during motion
- **Parallel angles** — variance of trajectory angles (high for translation, low for rotation)
- **Acceleration** — temporal variance of acceleration along each axis
- **Indicator vector** — the combined 8-dimensional feature per TSW

These indicator vectors are fed into a **Hidden Markov Model (HMM)** trained to classify four movement types: *reach*, *retreat*, *linear translation*, and *rotation*.

##### Stage 2 — Grasp Intention Recognition (eye-tracker + wrist camera)

A second HMM integrates the hand motion output with **gaze-based features**:

- **Saccade detection** — velocity of gaze position; low during fixations preceding a grasp
- **Object recognition** — a visual codebook (built offline via Vector Quantization on SURF features) is used to identify which object appears in the gaze camera
- **Hand likelihood** — posterior probabilities from Stage 1 HMMs

The key neuroscientific insight exploited here is that **gaze fixates on a target object before the hand begins to move** — and remains stable until the grasp is complete. By detecting this fixation-then-motion pattern across both cameras, the system can identify the desired object even before the hand reaches it.

---

#### Results

The system was evaluated on over 21,000 manually labeled frames across five everyday objects (cup, bottle, mug, box, deodorant), without any markers on object surfaces.

**Hand gesture recognition (Experiment 1)**

Average F-Score of **0.85** across ten HMM configurations and five objects. Retreat movements achieved the best recognition (~90%), while reach was sometimes confused with rotation due to similar visual patterns.

**Gaze + hand fusion for grasp detection (Experiment 3)**

| Class | TPR | FPR |
|---|---|---|
| Fixation | 83.3% | 1.9% |
| Reach-to-grasp | 92.5% | 16.7% |

**Object recognition**

| Object | TPR | FPR |
|---|---|---|
| Mug | 96.7% | 0.7% |
| Keys | 94.1% | 2.2% |
| Box | 96.1% | 1.5% |
| Card | 94.1% | 1.8% |
| **Mean** | **95.3%** | **1.6%** |

A key finding: the system could **predict the intended object before the hand reached it**, by leveraging gaze fixation as an anticipatory signal.

---

#### Applications & Future Work

The method is directly applicable to **human–computer interaction** and **assistive robotics** — particularly for users with neural degenerative disorders whose motor control is impaired but visual functions remain intact. It was also relevant to the BRAHMA project, a French multi-laboratory initiative developing robot assistance for upper limb motion.

Future work targets exploiting the redundancy between both viewpoints more explicitly, and testing with a larger and more diverse object set.

---

Cite: {% cite carrasco2012exploiting %}.