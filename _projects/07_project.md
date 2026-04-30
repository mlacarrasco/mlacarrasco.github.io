---
layout: page
title: Intelligent Image Recognition for SAG Mill Grinding Media
description: Computer vision prototype for automated detection, classification and measurement of steel grinding balls (MMS) (2017–2018).
img: assets/img/portafolio_proyectos_7.jpg
importance: 5
category: research
---

**Company:** Compañía Electro Metalúrgica S.A. (Elecmetal) — **Developer:** IO-link  
**Funding:** CORFO Innova Chile — Grant no. 16ITE1-70889 (120k USD)  
**Role:** Solution Architect & Developer

---

#### Context

SAG (Semi-Autogenous Grinding) mills are central to copper ore processing in Chile's large-scale mining operations. These mills are continuously fed with **Steel Grinding Media (MMS)** — steel balls of varying diameter and hardness — at an average rate of 30 tonnes per day, in campaigns lasting 4 to 6 months. The MMS represent the second-largest operational cost item in grinding, after energy, which itself is directly affected by MMS efficiency.

Despite this economic significance, MMS monitoring today is conducted in aggregate terms only: tonnes consumed per day, correlated with historical productivity indices. There is no practical, real-time, quantitative system capable of answering the questions that actually drive operational decisions:

- How many individual MMS units pass through the mill per day?
- What is the average residence time of an MMS inside the mill?
- What condition do MMS exit in — intact, fractured, or deformed?
- What is the exit diameter of each ball?
- Can worn MMS be reused in downstream grinding stages?
- Are there correlations between mill operating parameters and MMS output quality?

---

#### Solution

This project developed a **machine vision prototype** that automatically detects, classifies, and measures MMS exiting the SAG mill through the screen (harnero) area, operating 24/7 without human intervention and transmitting real-time KPIs to a cloud-based web dashboard.

##### Detection & Classification Algorithm

The algorithm pipeline processes video frames through four sequential stages:

**1. Template correlation:** For each frame, a non-parametric correlation against a set of MMS reference templates is computed pixel by pixel over a reduced transverse region of interest (ROI). This region-of-interest constraint reduces computational load while preserving detection accuracy in real time. Areas of maximum correlation are flagged as candidates.

**2. Neural network classification:** For each candidate region, concentric pixel strips (rays) are extracted from the center point at 0°–360°, concatenated into a single N-dimensional vector, and fed into a one-hidden-layer neural network that outputs: intact ball, fractured ball, oval ball, or deformed ball. This encoding abstracts away background noise and overlapping structures.

**3. Trajectory analysis:** Candidate regions are tracked across successive frames using a covariance analysis and distance-based clustering. A linear regression fit on each track determines whether the object's trajectory is consistent with natural harnero movement, discarding false positives. A "string algorithm" reduces combinatorial complexity in point-to-track assignment.

**4. Classification & diameter estimation:** Confirmed detections are classified by ball type and their diameter is estimated, contributing to a cumulative mass-of-steel register over time.

##### Distributed Camera Architecture

Due to the conflicting requirements of detection (real-time, lower resolution) and classification/measurement (high resolution, latency-tolerant), the system splits processing across two camera groups:

- **Detection cameras:** dedicated to real-time MMS detection, transmit (x,y) coordinates of confirmed candidates
- **Classification/measurement cameras:** receive coordinates, capture high-resolution crops, run the classification and diameter pipeline

A central field PC coordinates both groups, formats results, and transmits them to the remote server via Internet (or cellular backup). A web application hosted on the cloud server renders real-time KPI dashboards accessible from any device.

##### Software Stack

| Component | Technology |
|---|---|
| Algorithm prototyping | MATLAB + Image Processing Toolbox |
| Production implementation | C++ + OpenCV 3.2.0 |
| Application framework | Qt (cross-platform) |
| Field communication | Sockets (detection↔classification), HTTP/sqlite (field↔cloud) |
| Remote server | PHP + Apache + MySQL |
| Web dashboard | Custom web application |

##### Hardware

Field hardware was revised mid-project based on findings at Minera Centinela: the initially proposed distributed Raspberry Pi architecture was replaced by an **industrial PC with industrial cameras**, given the hostile mine environment (dust, vibration, outdoor exposure) and limited connectivity/power infrastructure at the harnero installation point.

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/video/myfile_0.30_Luz_Dia_co_0.8.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
</div>
<div class="caption">
    Real-time detection of steel grinding balls (MMS) in the SAG mill screen area. The algorithm identifies and classifies each ball as intact, fractured, oval, or deformed while estimating its diameter — operating at video frame rate under mine lighting conditions.
</div>

---

#### Project Progress (at reporting date)

| Stage | Description | Completion |
|---|---|---|
| Stage 1 — System Design | Architecture, hardware/software selection, lab setup | 100% |
| Detection algorithm | Template correlation + neural network + trajectory tracking | 100% |
| Classification & measurement | Ball type and diameter pipeline | 100% |
| Communication system | Field-to-cloud data pipeline | 100% |
| Remote server & database | Cloud storage infrastructure | 80% |
| Web visualization app | KPI dashboard | 100% |

Neural network training required field video captures at Minera Centinela under varying lighting, camera positions, and zoom levels — a step that proved critical given the algorithm's sensitivity to site-specific visual conditions. Based on this finding, the project moved Stage 4 (field validation) earlier in the timeline, conducting field visits in parallel with development to build a representative training image set.