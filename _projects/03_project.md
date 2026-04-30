---
layout: page
title: Inline Force Sensor for Electric Motor Inspection in Mining
description: Design, development and evaluation of a new inline force sensor and automated inspection protocol (2015–2018).
img: assets/img/portafolio_proyectos_3.jpg
importance: 3
category: research
related_publications: true
---

**Funding:** InnovaChile — CORFO Voucher (2015) | **Industry Partner:** PRODIN SpA  
**Role:** IT Engineer / Solution Designer & Developer

---

#### Context & Motivation

Chile accounts for roughly 30% of global copper production, making reliable mining equipment operation a matter of national economic importance. An unplanned stoppage of a SAG (Semi-Autogenous Grinding) mill costs between **10,000 and 50,000 USD per hour** — a figure that can be even higher depending on the fault location and type.

Electric motors are present in virtually every stage of the mining process: loading shovels, off-road trucks, conveyor belts, mills and crushers. These motors transmit current through **carbon brush systems** pressing against slip rings. When brush pressure is too high, mechanical wear accelerates; when too low, electric arcs develop, rapidly degrading the brush, the slip ring and the brush-holder itself. Maintaining correct spring tension — typically **7.84 N ± 0.05 N/cm²** for SAG mill brushes (50 × 25 × 16 mm) — is essential, yet no automated system existed to measure it.

Inspection today is performed manually by teams of two or more qualified operators following a LOTO (Lockout-Tagout) safety protocol with the motor fully stopped and de-energized. Measurements are recorded on paper forms, a process that is slow, error-prone, and prevents the accumulation of historical data needed for predictive maintenance models.

---

#### Solution: A New Inspection Protocol

This project redesigned the inspection protocol across two dimensions: hardware and software.

##### Hardware

**SCA Sensor (Brush-Holder Spring Sensor)**  
A custom sensor fabricated in ABS plastic, physically dimensioned to simulate a real carbon brush, is inserted directly into the brush-holder slot. Once inserted, a contact button activates the microcontroller and a Bluetooth antenna, enabling wireless communication with a mobile device. Key components include:

- **Honeywell FSS Low Profile** force sensor (sensitivity: 0.1 mV/g)
- **Olimexino 85S** microcontroller (300 µA consumption, −45°C to +85°C operating range)
- **RN42 Bluetooth** antenna for wireless data transmission
- **110 mAh LiPo battery** with SparkFun LiPo Charger — up to 8 hours of continuous use

The SCA firmware averages 100 consecutive readings and transmits the result wirelessly. Calibration against a precision PCE dynamometer yielded a linear force-voltage model (*force = voltage × 414.48*, R² = 0.995).

**Wireless Internal Caliper**  
A Kroeplin digital internal caliper was retrofitted with an Arduino Pro Mini, a USB Host Controller, and a Bluetooth module, enabling wireless transmission of internal brush-holder cavity dimensions directly to the mobile app.

##### Software

**Mobile App (APM — App Inventor)**  
The operator begins an inspection by scanning a QR code placed next to each brush-holder point. The QR code encodes the mine, mill, and inspection point identity. The app then guides the operator through activating each sensor, visualizing force and dimensional readings in real time, flagging out-of-tolerance values, and capturing a photo of the inspection point. All data is stored locally and synced to the cloud when connectivity is available.

**Automatic Report Generator (GAR — Desktop App)**  
Once the inspection is complete, a desktop application retrieves synced data from the cloud, presents it in spreadsheet format, and generates a structured PDF maintenance report with the full historical record of each brush-holder point.

---

#### Validation

A Finite Element Analysis (FEA) was performed using SolidWorks 2014 on the SCA sensor geometry under the 7.84 N spring load. The analysis used 21,870 high-order quadratic elements over 36,446 nodes. Maximum deformation was **0.003 mm** — negligible relative to the measurement scale — confirming the sensor's mechanical robustness and that its presence does not alter the spring force reading.

| Parameter | Value |
|---|---|
| Target spring force | 7.84 N ± 0.05 N/cm² |
| Calibration R² | 0.995 |
| Max. sensor deformation (FEA) | 0.003 mm |
| SCA battery life | 8 hours continuous |
| Caliper battery life | 24 hours continuous |
| Force conversion model | force = voltage × 414.48 |

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/portafolio_proyectos_3.jpg" title="SCA sensor prototype and inspection setup" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    SCA inline force sensor prototype — designed to simulate a real carbon brush while wirelessly measuring spring tension inside the brush-holder.
</div>

---

#### Future Work

Next steps include integrating the SCA force sensor and the internal caliper into a single unified instrument, reducing inspection time to a single insertion step. The accumulated historical dataset also opens the door to machine learning-based predictive failure models for brush-holder maintenance.

---

Cite: {% cite carrasco2019brush %}.