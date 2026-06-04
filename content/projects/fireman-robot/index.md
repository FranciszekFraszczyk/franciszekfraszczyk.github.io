---
title: "Autonomous Fireman Climbing Robot"
description: "A mechanical scaling platform engineered with a custom trapezoidal climbing linkage, active microswitch limit tracking, and a self-locking rack-and-pinion payload gripper."
date: 2024-02-19
showAuthor: false
featured: true
thumbnail: "featured.jpg"
---

### Project Overview

<div style="text-align: justify;">
Developed as part of the MM310 Product Design module at Dublin City University, this project involved the complete design specification, kinematic synthesis, and structural fabrication of a specialised "Fireman Robot" designed to ascend a vertical ladder structure. The system was engineered to mechanically climb a 50mm x 50mm central upright box section, actively register rungs using integrated electromechanical limit monitoring, and securely retrieve an external payload at the apex before safely descending.
</div>

### Technical Engineering Stack

<div style="text-align: justify;">

* **Structural Material:** 5mm Poly(methyl methacrylate) / Acrylic Sheet (Precision Laser Cut)
* **Kinematic Linkage System:** Optimised Four-Bar Trapezoidal Linkage Configuration
* **Actuation Suite:** High-Torque DC Geared Drive Motors paired with a Micro Servo Core
* **Sensor Infrastructure:** Miniature Rolling-Lever Microswitches (for absolute physical edge and rung detection)
* **Payload Mechanism:** Custom Rack-and-Pinion Sliding Gripper Assembly
* **Design & Analysis Software:** SolidWorks (Parametric 3D Modelling), Ansys (Finite Element Analysis for structural stress boundaries)

</div>

---

### Core Subsystems & Implementation

#### 1. Trapezoidal Four-Bar Climbing Linkage

<div style="text-align: justify;">
To achieve stable, vertical climbing vectors along a standard hollow box column, a critical design choice was made to synthesise a custom trapezoidal linkage mechanism. Compared to alternative triangular or continuous track configurations evaluated in the initial engineering matrix, this four-bar geometric layout provided superior mechanical advantage:
* **Structural Load Pathing:** The trapezoidal layout spreads operational forces evenly across the main chassis plates, eliminating horizontal moments that could cause binding against the central upright track.
* **Passive Grip Integration:** As the primary drive links pivot, the geometry converts a portion of the vertical motor torque into direct gripping force, clamping the support brackets tighter against the column during maximum vertical extension phases.
</div>

#### 2. Electro-Mechanical Rung Tracking Logic

<div style="text-align: justify;">
Autonomous alignment and milestone targeting were governed entirely by physical limit monitoring, removing the need for error-prone optical tracking in harsh physical environments:
* **Microswitch Array Configuration:** Rolling-lever microswitches were integrated directly into custom-designed structural housings mounted on the upper wheel brackets.
* **Absolute Feedback Loops:** As the climber scales the column, the physical rungs mechanically actuate the switch arms. The resulting state transitions provide clean, absolute feedback to track vertical progress, index specific step layers, and safely halt upward drive operations once the destination threshold is reached.
</div>

#### 3. Self-Locking Payload Gripper Assembly

<div style="text-align: justify;">
Retrieving the payload at the apex of the structure required a lightweight, structurally rigid mechanical interface capable of maintaining an unpowered grip:
* **Rack-and-Pinion Mechanics:** A precision rack-and-pinion gear profile was designed to convert rotational servo inputs into linear sliding finger paths.
* **Structural Box Finger Profile:** The sliding grab arms were manufactured using a high-contact box profile lined with high-friction dampening pads, allowing the mechanism to mechanically trap the payload and maintain absolute control without drawing excessive stall currents from the servo system.
</div>

#### 4. FEA Structural Optimisation & Laser Fabrication

<div style="text-align: justify;">
Weight minimisation and structural stress management were handled concurrently through exhaustive computational engineering loops prior to physical manufacture:
* **Finite Element Analysis (FEA):** Crucial high-stress nodes—specifically the main axle bearing mounts and the bottom damper linkage joints—were analysed under maximum simulated stall torques within Ansys. Material was selectively filleted and pocketed based on von Mises stress plots to eliminate points of failure.
* **Precision Acrylic Fabrication:** The finalised chassis maps, linkages, and stabilizer components were exported as vector files for high-precision laser profiling on 5mm acrylic sheets, ensuring dimensional tolerances within 0.1mm to eliminate structural play.
</div>

---

### System Demonstrations

To see the climbing robot executing its vertical navigation routines, watch the video demonstrations below:

{{< youtube id="x4oyXfnyspo" >}}


