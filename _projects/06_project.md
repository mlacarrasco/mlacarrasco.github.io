---
layout: page
title: IoT-Based Remote Monitoring for Critical Infrastructure
description: Design and deployment of a real-time IoT monitoring system for industrial freezer units and server rooms (2017–2018).
img: assets/img/portafolio_proyectos_6.jpg
importance: 4
category: research
---

**Client:** Edocere — Walmart Chile (2017–2018)  
**Role:** Solution Architect & Developer

---

#### Diagnosis & Problem

Walmart Chile's store infrastructure included electro-mechanical systems with no remote monitoring capability. The specific failure points identified during the diagnostic phase were:

- Electrical backup systems (generators) that could fail silently without reporting their status, cascading into failures in dependent subsystems
- Refrigeration units, cold chambers, and compressor doors with no sensor coverage for temperature, humidity, or access events
- Significant economic losses caused by undetected equipment failures and lack of real-time state information
- No centralized information system capable of generating automatic status reports across stores

---

#### Solution: Three-Phase Deployment

The project was structured as a two-store pilot across three months, covering analysis, development, and commissioning.

**Phase I — Diagnosis & Technology Selection**  
On-site analysis of existing refrigeration systems in two Walmart Chile supermarkets. This phase mapped available power tapping points, evaluated communication options that could operate independently from the store's main electrical supply, and defined sensor selection criteria and current technological constraints.

**Phase II — Development**  
Microcontroller and sensor programming for device monitoring, communication system setup with a structured data generation protocol, data analysis pipeline, and 3D-designed enclosures for field-robust equipment mounting. Sensor nodes were built around Arduino R3 boards with LiPo batteries and LiPoRider charging circuits, enabling operation during power outages.

**Phase III — Commissioning & Validation**  
System installation, automatic report generation, remote control activation, sensor calibration, and data validation. Final pilot conclusions documented for potential rollout to additional stores.

---

#### Hardware Stack

| Layer | Components |
|---|---|
| Communication | GPRS modems, Entel PCS data plan |
| Environmental sensors | Temperature, humidity |
| Electrical sensors | Current consumption |
| Access sensors | Door open/close status |
| Microcontrollers | Arduino R3 |
| Power | LiPo battery + LiPoRider (backup-capable) |
| Enclosures | Custom acrylic / ABS (3D designed) |

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_6.jpg" title="IoT monitoring system overview" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_walmart/foto_1.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_walmart/foto_2.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_walmart/foto_3.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_walmart/foto_5.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
<div class="caption">
    Deployed sensor nodes and web monitoring dashboard. Battery-backed GPRS nodes transmit environmental and electrical readings from refrigeration units and server rooms to a centralized reporting platform.
</div>

---

#### Outcome

The pilot demonstrated that store-wide environmental and electrical monitoring could be deployed rapidly using low-cost IoT hardware with GPRS connectivity independent of store network infrastructure. The battery-backed design ensured continuous monitoring during the same power outage events the system was built to detect — eliminating the blind spot that had previously made generator failures invisible until downstream systems failed.