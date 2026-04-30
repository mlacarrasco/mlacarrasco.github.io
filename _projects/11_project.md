---
layout: page
title: Online Control System for Manufacturing
description: Real-time production control system for PRODIN, a mining spare parts manufacturer — integrating Job Shop optimization, operator interfaces, and live workshop monitoring (2016–2017).
img: assets/img/portafolio_proyectos_11.jpg
importance: 5
category: research
---

**Company:** [PRODIN](https://prodin.cl/) Ltda. — **Partner:** Adolfo Ibáñez University (UAI)  
**Funding:** CORFO Innova Chile — Voucher Grant no. 14-VIP35679 (100k USD)  
**Role:** Solution Architect & Developer

---

## Context

[PRODIN](https://prodin.cl/) Ltda., a Chilean manufacturer of spare parts for the mining industry, faced significant inefficiencies in its production process: late detection of delays, bottlenecks, idle machinery hours, and high energy costs. To address these issues, PRODIN formed a strategic alliance with Adolfo Ibáñez University (UAI), funded by CORFO, with the goal of incorporating information technologies into its production management.

---

## Objective

Develop a **real-time production control system** that increases PRODIN's productivity and competitiveness in both domestic and international markets.

---

## What Was Built

The project was structured into two main blocks.

### 1 — Mathematical Optimization Model
*(Led by the UAI Operations Research Group)*

A **binary programming model** was developed to solve the workshop scheduling problem — a classic **Job Shop** formulation — with the objective of assigning tasks to machines while minimizing delivery times across manufacturing orders. The model incorporates:

- Precedence constraints between operations
- Machine capacity limits
- Worker availability (18 machines available, but only 9 operators on staff — so no more than 9 machines can run simultaneously)

The primary solver was implemented in **Python using Gurobi**. A **free greedy heuristic** was also developed as an alternative for deployments without a commercial license. Monte Carlo analysis showed that processing time estimation errors below 15% yield results within acceptable ranges.

### 2 — Visualization & Data Capture Tools
*(Led by the UAI IT Group)*

Three components were built:

**2.1 TPM Module (Tree Production Module)**  
A desktop application that reads XLS files exported from PRODIN's CAD models and transforms them into production trees with explicit precedence relationships between tasks. The engineer can manually complete missing links and export the result in a format compatible with SAP.

**2.2 Online Web Platform**  
An administration portal allowing users to load and manage weekly manufacturing orders, trigger the optimization model, and monitor order progress in real time. Includes both a per-workstation view and a global workshop overview for administrators.

**2.3 Operator Interface (Tablet-based)**  
Each operator can identify themselves, view their assigned task (including the technical PDF drawing), and log the start, pause, interruption, and completion of each operation — feeding live data back into the central control system.

---

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proyecto_PRODIN/esquema_logico.jpg" title="System logical schema" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/proyecto_PRODIN/ouput_interfaz_utilitaria_27_nov.jpg" title="Web platform interface" class="img-fluid rounded z-depth-1" %}
    </div>
</div>
<div class="caption">
    Left: Logical architecture of the integrated control system. Right: Web platform interface showing production order monitoring.
</div>

---

## Technologies

| Layer | Technology |
|---|---|
| Optimization | Python, Gurobi, custom greedy heuristic |
| Web backend | CodeIgniter (PHP) |
| Shop floor terminals | Raspberry Pi + LCD monitors |
| Operator interface | Tablet-based web app |
| ERP integration | SAP-compatible export |

---

## Key Results

- Optimization model capable of solving orders with **hundreds of tasks in a few minutes**
- Monte Carlo analysis confirmed robustness to estimation errors below 15%
- All modules fully integrated and delivered to the PRODIN team
- Fixed workstation costs reduced by using Raspberry Pi boards instead of conventional PCs

---

## Limitations & Future Work

The optimal solver requires a **commercial Gurobi license**; the greedy heuristic is available as a fallback. The TPM module is currently desktop-only and does not support undo operations. A unified single-environment platform was identified as the natural next step, though it falls outside the scope of the current contract.