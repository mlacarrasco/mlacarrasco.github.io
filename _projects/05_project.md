---
layout: page
title: Particle Size Distribution via In-Depth Optical Analysis
description: Design of a vision-based optical sensor integrated into a CPTu geotechnical probe (2018).
img: assets/img/portafolio_proyectos_5.jpg
importance: 5
category: research
---

**Funding:** UAI-2030 — CORFO Technology Transfer (2018)  
**Principal Director:** Ricardo Moffat, Universidad Adolfo Ibáñez  
**Role:** Co-director & Researcher

---

#### Context

Cone Penetration Tests (CPTu) are standard geotechnical site investigation tools that measure soil stress and pore water pressure by pushing a cylindrical probe into the ground up to 30 meters or more. While CPTu probes yield continuous profiles of stress and deformation parameters, they cannot directly provide the **particle size distribution (PSD)** of the soil — information that is equally critical for structural design, erosion analysis, and soil liquefaction assessment.

Today, PSD determination requires additional boreholes to extract physical soil samples, which are then transported to a laboratory for conventional granulometric analysis (sieve and hydrometer tests). This adds significant time and cost to every geotechnical investigation, and makes real-time in-situ characterization impossible.

---

#### Proposed Solution

This project proposes integrating a **computer-vision-based optical sensor** directly into a CPTu probe, capable of capturing digital images of soil particles at successive depths and computing the granulometric curve in situ — eliminating the need for separate sampling campaigns.

##### Key Technical Challenges

Embedding a camera inside a CPTu probe introduces three simultaneous constraints that make this a genuinely hard engineering problem:

- **Mechanical robustness:** the probe tip must withstand tangential forces of up to **22 tons** at depth, requiring a high-strength transparent window or glass cone geometry
- **Illumination in a closed environment:** no external light is available underground; a compact internal illumination system must project uniform light onto the particle sample within a dark chamber
- **High-precision imaging at microscale:** soil particles of interest range from **75 μm to 2 mm**, demanding a high-definition CCD sensor with precise focus at very short working distances and in confined geometry

##### Approach

**Phase 1 — Laboratory optical characterization**  
A dark-chamber prototype with an internal RGB LED array (digitally controlled via microcontroller for both intensity and color) is used to study how light at different wavelengths interacts with soil minerals. It is well established that incident light on minerals produces a wavelength-dependent reflectance response. The hypothesis is that pixel intensity captured by an infrared-filter-free CCD sensor across a broader spectral range can discriminate particle types and sizes more effectively than conventional white-light imaging.

Experiments are conducted on soil samples of known particle size (75 μm to 2 mm) to build a model linking spectral response to granulometric properties. This model is then integrated into a robust segmentation pipeline.

**Phase 2 — Probe integration**  
The validated optical system is embedded into a CPTu-compliant probe following ASTM D5778 specifications, building on the VisCPT framework as a reference design. The system must capture usable particle images continuously as the probe advances through soil layers.

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_5.jpg" title="Computer vision algorithm for soil particle size measurement" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Computer vision algorithm for in-situ soil particle size measurement. The system segments individual particles from CCD images captured inside the probe dark chamber, then reconstructs the granulometric distribution curve without laboratory sampling.
</div>