---
title: "Automated Guided Vehicle (AGV) "
date: 2022-03-15
description: "A compact Automated Guided Vehicle optimised for spatial efficiency, geometric Ackerman steering, and TCRT5000 infrared line tracking."
summary: "An efficient, small-footprint Automated Guided Vehicle featuring an optimised golden-ratio chassis layout, precise mechanical trapezoidal steering, and calibrated infrared optical tracking."
tags: ["Mechatronics", "Automation", "Embedded Systems", "PCB Trace", "Hardware"]
categories: ["Projects"]
showAuthor: false
featured: true
thumbnail: "featured.jpg"
---

## Project Overview

The **Sigmobile AGV** is a compact Automated Guided Vehicle built with an emphasis on spatial efficiency and precise physical tracking systems. Developed within a three-person engineering team, the core objective was minimizing effective dimensions to allow for fleet operation inside modern smart warehouse environments. 


---

## Technical Specifications & Calculations

### 1. Space-Optimized Chassis Layout
To maintain an aesthetic balance and structural stability, the chassis footprint was developed using proportional dimensional bounds:
*   **Base Footprint:** $240\text{ mm} \times 150\text{ mm}$ (approximating the Golden Ratio $\phi \approx 1.618$).
*   **Ground Clearance:** Kept intentionally low to optimize center of mass stability and minimize vertical volume profiles.

### 2. Ackerman Steering Optimization (My Focus)
To avoid wheel scrubbing and ensure smooth tracking trajectories, the steering geometry approximates the **Ackerman Steering Curve** via a mechanical trapezoidal linkage loop.

```text
       Servo Arm Linkage Mechanics
                  SERVO
                    │
              ┌─────┴─────┐
              │           │
       ┌──────┴───┐   ┌───┴──────┐
       │ Trapezoidal Linkage     │
   (Wheel)                     (Wheel)
