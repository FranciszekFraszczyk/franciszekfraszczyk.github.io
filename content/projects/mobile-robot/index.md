---
title: "Autonomous Mobile Robot"
description: "An autonomous line-tracking mobot featuring embedded navigation, synchronous server communication, and a custom web remote-control interface."
date: 2024-02-22
showAuthor: false
featured: true
thumbnail: "featured.jpg"
---

### Project Overview

<div style="text-align: justify;">
Developed as part of the EE303 Mobile Robotics module at Dublin City University, this project involved the design, manufacturing, and firmware optimisation of an autonomous mobile robot ("Mobot"). The system was engineered to autonomously navigate a physical track, cross marked intersection checkpoints, and perform precision parking operations against track boundary structures. When the robot reached its destination, the car's position would update on the server and the next destination point would be sent to the robot.
</div>

### Technical Engineering Stack

<div style="text-align: justify;">

* **Microcontroller Platform:** Texas Instruments MSP432 LaunchPad
* **Wireless Transceiver Module:** CC3100 SimpleLink Wi-Fi Network Processor
* **Motor Control System:** DRV8835 Dual Motor Driver Carrier (Dual H-Bridge IC)
* **Sensor Arrays:** Front-mounted 5-Channel Infrared (IR) Reflectance Sensor PCB, Rear Analogue Proximity Sensor
* **Power Subsystem:** 9.6V battery pack paired with a DC-to-DC buck converter
* **Firmware Environment:** C/C++ (Energia IDE Framework)
* **Web Telemetry Stack:** Asynchronous JavaScript and XML (AJAX), JavaScript, and Custom CSS (for the remote control interface framework)

</div>

---

### Core Subsystems & Implementation

#### 1. Sensor Calibration & Smoothing Framework

<div style="text-align: justify;">
To limit signal bounce and prevent erratic over-steering from high-frequency analogue line tracking spikes, a low-pass software smoothing function was implemented. The sensor suite captures data streams in the range of <code>50-150</code> for light/white surfaces and <code>600-900</code> for dark/black boundaries:
</div>

* Reads values natively via five concurrent `analogRead()` mapping pipelines.
* Generates a moving average across every ten raw input streams using a dedicated loop matrix to maintain stable tracking data arrays.
* Integrated a `1k Ohm` resistor integrated circuit (IC) to isolate sensory boards from voltage surges.

#### 2. Dual-Axis Line Tracking Logic

<div style="text-align: justify;">
The navigation script uses the data arrays to dynamically adjust the DC motors. By configuring a threshold limit of `150` to declare a valid track intersection, the bot actively calculates spatial adjustments:
</div>

* **Directional Adjustments:** Micro-steering corrections execute on the fly; triggering the interior left sensor commands a localised left turn, while triggering the interior right sensor commands a right turn.
* **Horizontal Stop Points:** Whenever the outer boundary limits (Sensors 1 and 5) simultaneously identify a white horizontal line crossbar, the firmware triggers a complete zero PWM electronic `brake()` to register at the junction checkpoint.

#### 3. State Engine & Decision Tree Mapping

<div style="text-align: justify;">
The main firmware orchestrates global path planning via an explicitly designed nested state engine:
</div>

* Manages positions using variables for **Previous Position (`ppos`)**, **Current Position (`cpos`)**, and **Next Position (`npos`)**.
* A dedicated evaluation routine, `uturnck()`, analyses the robot's position prior to motion execution to test if a 180-degree orientation flip on the spot is required before embarking on the next shortest-path switch case.

#### 4. Wireless Server Telemetry & Dynamic Routing

<div style="text-align: justify;">
Real-time navigation coordination was handled over local network protocols using the CC3100 Wi-Fi chipset. The communication layer executed a robust, synchronous data exchange loop:
</div>

* **Network Initialisation:** Established reliable network handshakes using a persistent blocking routine (`WL_CONNECTED`) to guarantee connection stability before initiating movement.
* **Server-Driven Coordination:** Transmitted real-time checkpoints via standard HTTP `POST` requests (`/api/arrived/...`). Upon reaching a designated track junction, the robot immediately updated its position on the centralised server, which processed the state change and pushed back the coordinates for the next destination.
* **Payload Parsing & Error Handling:** Parsed text-based server responses to catch and resolve non-`200 OK` status codes via an automated retry fallback. The firmware dynamically decoded incoming instruction strings to safely flag a completed route execution.

#### 5. Proportional Distance Braking & Parking

<div style="text-align: justify;">
The reverse mechanical sub-routine leverages raw inputs from the rear analogue distance sensor. The proximity controller utilises dynamic deceleration to execute a safe parking sequence:
</div>

* Regulates torque profiles in reverse proportional to proximity data.
* Implements a mechanical threshold floor of `30` PWM to prevent the motors from stalling due to friction constraints, completely disabling drive operations once physical alignment steps are finalised.

---

### System Demonstrations

To see the mechatronics assembly executing its live track routines, watch the video demonstrations below:

#### 1. System Integration & Line-Tracking Testing
Shows the preliminary sensor calibration routines, boundary detection, and chassis adjustment testing on a simplified physical track layout.

{{< youtube id="h9Hx90FAKKc" >}}

#### 2. Reverse Parking Manoeuvre
Demonstrates the real-time proximity calculations in action, showing the robot dynamically decelerating and parking flush against the track boundary wall.

{{< youtube id="dASNRNrvkik" >}}

#### 3. Full Autonomous Run
The complete, end-to-end operational trial showing successful intersection handling, centralised server communication, and dynamic route execution.

{{< youtube id="fSrWPY9GI_4" >}}
