---
layout: page
title: Real-Time Visual Inspection for Poultry Processing
description: Computer vision MVP for automated fat segmentation and quality grading of turkey carcasses on a live production line — (2022).
img: assets/img/portafolio_proyectos_12.jpg
importance: 6
category: research
---

**Client:** [IaLINK](https://www.ialink.cl) — AI solutions for food production & health  
**Funding:** MVP — IaLINK VERIA-CLOUD  
**Role:** Machine Learning Developer

---

#### Context

IaLINK is a Chilean technology company specializing in AI-powered inspection systems for manufacturing and food production. Their flagship industrial platform, **VERIA-CLOUD**, targets high-speed, repetitive production processes where human visual inspection is too slow or inconsistent to meet quality standards — replacing it with real-time computer vision that monitors continuously and flags anomalies automatically.

This project extended VERIA-CLOUD into poultry processing, one of Chile's largest food production sectors, in collaboration with the country's leading turkey processor.

---

#### Objective

Develop a real-time in-line inspection tool capable of operating directly within an active turkey processing facility — under strict requirements for inspection accuracy, throughput, and speed. As carcasses move along the production line in front of a camera, the system must automatically segment fat regions on each carcass, estimate a fat percentage per unit, and identify the appropriate cutting zones based on fat distribution.

The system operates at production-line speed with no manual intervention, providing per-carcass quality data that enables objective, consistent grading at a scale and pace that human inspectors cannot match.

---

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/test_segmentacion.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Real-time fat segmentation on poultry carcasses. The algorithm detects and segments fat regions frame-by-frame as units pass the camera, computing a fat percentage estimate and flagging optimal cutting zones for downstream processing.
</div>

> **Status:** MVP — currently in validation phase within a live production environment.