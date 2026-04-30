---
layout: page
title: Machine Learning for Blueberry Production Under Climate Change
description: Predictive models for harvest timing and quality of the Rocío blueberry variety using IoT sensor networks - Hortifrut & UAI, CORFO (2018–2020).
img: assets/img/portafolio_proyectos_8.jpg
importance: 1
category: research
---

**Company:** Hortifrut S.A. — **Research partner:** Universidad Adolfo Ibáñez (UAI)  
**Funding:** CORFO Contrato Tecnológico — Grant no. 17COTE83081 (~300k USD)  
**Role:** Solution Architect & Developer

---

#### Context

Hortifrut S.A. is the world's largest blueberry producer and exporter, with operations across Chile, Mexico, Spain, Peru, Brazil, and the USA — covering 1,403 ha and commercial presence in 37 countries. The company faces a specific and economically significant problem with the **Rocío variety**, developed in Spain and characterized by very low cold-hour requirements, which allows early harvest entry. However, Rocío's adaptation to Chilean conditions is erratic and its productive potential is not consistently realized.

Climate change is making this worse. Germánwatch places Chile among the ten countries most affected by climate-related weather events. Global models project temperature increases of 2–7°C by end of century, precipitation reductions of 5–15% in the next 30 years in central Chile, and accelerated phenological cycles. In practice, the 2016–2017 harvest of blueberries was advanced by four weeks due to high temperatures, causing a significant price drop. Currently, monitoring is conducted by human experts supported by meteorological station data, producing some empirical rules about growth rates and harvest windows — but these rules capture only linear relationships and cannot combine the full set of interacting variables.

---

#### Objective

Develop and validate an automatic system to **predict harvest quality and timing** for the Rocío blueberry variety using machine learning, based on multi-site historical environmental data and a controlled experimental station.

---

#### Multi-Site Data & IoT Monitoring

Hortifrut already operates automatic sensor networks at six Rocío cultivation sites: **Vicuña, Putaendo, Los Ángeles** (Chile), **Peru, Mexico, and Spain**. Each site records a continuous stream of environmental variables used as model inputs:

- Air temperature and humidity
- Soil moisture and salinity
- Soil temperature
- Light levels (PAR)
- CO₂ concentration
- Irrigation drainage

For this project, **40 instrumented pots** were deployed north of San Felipe, monitored remotely via a Cayenne IoT platform. The system provides real-time control of environmental conditions and automatic capture of plant-level response variables. Two climate sub-stations were built in Putaendo — containerized controlled-environment units with regulated temperature, irrigation, humidity, photoperiod (16/6 h), and precision LED lighting (200 µmol m⁻²s⁻¹) — to simulate projected climate scenarios and generate training data for conditions underrepresented in historical records.

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_8.jpg" title="Blueberry monitoring system overview" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/instalacion_1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/instalacion_2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/instalacion_3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/img/proyecto_hortifrut/estanque_video.mp4" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/estanque_1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/estanque_2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hortifrut/instalacion_4.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    IoT monitoring infrastructure: instrumented pots with environmental sensors (top), controlled climate sub-stations in Putaendo for simulating future climate scenarios and generating new training data (bottom).
</div>

---

#### Predictive Modeling Methodology

The ML pipeline addresses five technical challenges:

**1. Data repository construction** — Historical records from six geographic locations are consolidated, cleaned (outlier rejection, missing data imputation via EM algorithm), and enriched with derived features such as rolling averages and cross-variable interactions (e.g., age × heart rate analogs for plant phenological stage). All data is formatted into a model input matrix using R.

**2. Exploratory analysis & clustering** — Unsupervised methods (k-means, self-organizing maps) identify natural groupings in the multi-site data, revealing how harvest timing and quality vary across climate clusters. This step is critical for understanding which variables carry the most discriminatory power.

**3. Predictive model construction** — Multiple ML model families are evaluated and compared, including Extreme Learning Machines (ELM), Random Forests, Support Vector Machines (SVM), Neural Networks, and Naïve Bayes. Ensemble methods and hybrid model combinations are also explored. Imbalanced class handling (via SMOTE and related techniques) is applied when certain phenological events are underrepresented in historical data.

**4. Molecular markers** — Plant tissue samples are analyzed by qRT-PCR to measure expression of flowering, fruiting, and stress marker genes — providing physiological ground truth beyond what environmental sensors alone can capture.

**5. Experimental validation** — Controlled sub-station experiments expose Rocío plants to simulated future climate conditions, validating model predictions against observed plant responses and generating new training examples for rare climate scenarios.

---

#### Key Research Hypothesis

A machine learning model trained on historical atmospheric records from six geographically diverse sites can predict the quality and harvest timing of Rocío blueberries at high accuracy — and remain valid under climate projections that lie outside the historical training distribution, by incorporating controlled experimental data as synthetic training examples.