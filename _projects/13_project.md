---
layout: page
title: Real-time monitoring of concrete curing
description: Sensor network system for real-time monitoring of concrete curing (2022).
img: assets/img/portafolio_proyectos_13.png
importance: 7
category: research
---
 
**Role:** Developer and Solution Architect

---

#### Context

In concrete construction, monitoring temperature and humidity during curing is critical to determine the exact setting point of the mix. Traditional methods rely on a supervisor physically inspecting each sensor at discrete time intervals, capturing only point-in-time readings — leaving the process blind between visits.

A prior laboratory campaign evaluated multiple sensor configurations, and a pilot deployment of four temperature and humidity sensors was carried out on a massive concrete structure (~950 BSA m³, February 2016), yielding results consistent with independent measurements from DICTUC on the same site.

Despite this, **the industry still lacks a real-time remote monitoring system**, creating a gap between the data available and the decisions that need to be made on-site.

---

#### Objective

Design and deploy a wireless sensor network — combining MESH radio and GPRS connectivity — embedded directly in the concrete structure during curing. The system continuously streams temperature and humidity data to a central server, enabling real-time visibility and predictive analytics of concrete curing conditions without requiring on-site personnel to collect readings manually.

---

<div class="row mt-3">
   <div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hormigon/Imagen_2_v.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hormigon/Imagen_3_v.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hormigon/Imagen_4_v.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
</div>
</div>

<div class="row mt-3">
    <div class="col-sm mt-3 mt-md-0">
        {% include video.liquid path="assets/img/proyecto_hormigon/Imagen_5_h.jpg" class="img-fluid rounded z-depth-1" controls=true autoplay=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hormigon/Imagen_6_h.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid path="assets/img/proyecto_hormigon/Imagen_7_h.jpg" class="img-fluid rounded z-depth-1" zoomable=true %}
    </div>
    
</div>
<div class="caption">
    Central unit components include the server box, LipoBoost shield, GPRS modem, current sensor, temperature and humidity sensor, relay, and supporting metallic mounts — all integrated for field deployment.
</div>

> **Status:** MVP — currently in validation phase within a live production environment.