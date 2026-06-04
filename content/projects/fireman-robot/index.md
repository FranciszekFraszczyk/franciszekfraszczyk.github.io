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
Developed as part of the MM310 Product Design module at Dublin City University, this project involved the complete design specification, kinematic simulation, and mechanical fabrication of a specialised "Fireman Robot" designed to ascend a vertical ladder structure. The system was engineered to mechanically climb a 50mm x 50mm central upright box section, actively register rungs using electromechanical limit switches, and securely deliver a jug of water to the apex.
</div>

### Technical Engineering Stack

<div style="text-align: justify;">

* **Actuation Suite:** High-Pressure Pneumatic Double-Acting Cylinder (50mm Stroke Extension) 
* **Control Valve Infrastructure:** 5/2-Way Single Solenoid Directional Control Valve 
* **Kinematic Linkage System:** Optimised Four-Bar Trapezoidal Linkage Configuration
* **Sensor Infrastructure:** Rolling-Lever Microswitches housed in custom adjustable enclosures
* **Fluid Damping Subsystem:** Quad Extension Spring Array paired with a custom-machined Dashpot 
* **Design & Simulation Suite:** SolidWorks

</div>

---

### Core Subsystems & Implementation

#### 1. Trapezoidal Four-Bar Climbing Linkage

<div style="text-align: justify;">
To scale the ladder under strict spatial constraints, the robot required a mechanism capable of turning local cylinder extensions into vertical steps. Because the physical ladder rungs were pitched <code>52mm</code> apart and the pneumatic piston’s absolute stroke length was limited to <code>50mm</code>, a direct linear lift was impossible. To resolve this 2mm shortfall, a custom four-bar trapezoidal linkage system was designed.
</div>

<div style="text-align: center; margin: 20px 0;">
  <img src="linkage-system.jpg" alt="Trapezoidal Linkage" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 1.1: SolidWorks CAD simulation of the four-bar trapezoidal linkage synthesis.</p>
</div>

#### 2. Electro-Mechanical Rung Tracking Logic

<div style="text-align: justify;">
Autonomous operational safety, state changes, and peak stopping were governed entirely by limit switch monitoring, avoiding complex optical tracking sensors:
</div>

* **Linkage State Switching:** Miniature rolling-lever microswitches were integrated directly into custom-designed structural housings mounted near the linkage brackets. Rather than counting rungs or processing numerical variables, these switches tracked physical linkage extension limits to actively alternate the system between the extension/retraction pneumatic states.
* **Absolute Apex Holding Logic:** A dedicated limit switch was positioned to trigger explicitly upon reaching the ladder's peak. Once this absolute upper threshold was contacted, the control circuit permanently locked the directional solenoid valve into a static hold sequence, safely stopping all vertical travel and securely suspending the chassis without overshooting.
* 
<div style="text-align: center; margin: 20px 0;">
  <img src="limitswitches.jpg" alt="Microswitch Array" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 2: Custom microswitch integration and mounting configuration for automated mechanical routing feedback.</p>
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


