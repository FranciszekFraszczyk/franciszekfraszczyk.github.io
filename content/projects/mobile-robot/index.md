---
title: "Autonomous Mobile Robot"
description: "An autonomous line-tracking mobot featuring embedded finite-state navigation, synchronous server communication, and a custom remote-control telemetry interface."
date: 2026-06-04
showAuthor: false
featured: true

# Links the local image package asset seamlessly 
thumbnail: "featured.jpg"
---

### Project Overview
[cite_start]Developed as part of the EE303 Mobile Robotics module at Dublin City University, this project involved the design, manufacturing, and firmware optimization of an autonomous mobile robot ("Mobot")[cite: 1, 3]. [cite_start]The system was engineered to autonomously navigate a complex physical track network, cross marked intersection checkpoints, dynamically coordinate destination routing with a centralized web server via wireless networks, and perform precision parking operations against track boundary structures[cite: 3, 13].

### Technical Engineering Stack
* [cite_start]**Microcontroller Platform:** Texas Instruments MSP432 LaunchPad [cite: 12]
* [cite_start]**Wireless Transceiver Module:** CC3100 SimpleLink Wi-Fi Network Processor [cite: 12, 156]
* [cite_start]**Motor Control System:** DRV8835 Dual Motor Driver Carrier (Dual H-Bridge IC) [cite: 18, 28, 410]
* [cite_start]**Sensor Arrays:** Front-mounted 5-Channel Infrared (IR) Reflectance Sensor PCB [cite: 32, 52][cite_start], Rear Analog Proximity Sensor [cite: 129, 137]
* [cite_start]**Power Subsystem:** 9.6V Nickel-Metal Hydride (NiMH) battery pack paired with a DC-to-DC buck converter [cite: 25]
* [cite_start]**Firmware Environment:** C/C++ (Energia IDE Framework) [cite: 157]

---

### Core Subsystems & Implementation

#### 1. Sensor Calibration & Smoothing Framework (`Sense()`)
[cite_start]To limit signal bounce and prevent erratic over-steering from high-frequency analog line tracking spikes, a low-pass software smoothing function was implemented[cite: 62, 63]. [cite_start]The sensor suite captures data streams in the range of `50-150` for light/white surfaces and `600-900` for dark/black boundaries[cite: 60]:
* [cite_start]Reads values natively via five concurrent `analogRead()` mapping pipelines[cite: 57, 93].
* [cite_start]Generates a moving average across every ten raw input streams using a dedicated loop matrix to maintain stable tracking data arrays[cite: 69].
* [cite_start]Integrated a `1k Ohm` resistor integrated circuit (IC) to isolate sensory boards from voltage surges[cite: 35, 36].

#### 2. Dual-Axis Line Tracking Logic
[cite_start]The navigation script uses the data arrays to dynamically regulate the dual DC motors[cite: 91, 93]. [cite_start]By configuring a threshold limit of `150` to declare a valid track intersection, the bot actively calculates spatial adjustments[cite: 94, 95]:
* [cite_start]**Directional Adjustments:** Micro-steering corrections execute on the fly; triggering the interior left sensor commands a localized left turn, while triggering the interior right sensor commands a right turn[cite: 82, 83].
* [cite_start]**Horizontal Stop Points:** Whenever the outer boundary limits (Sensors 1 and 5) simultaneously identify a white horizontal line crossbar, the firmware triggers a complete zero PWM electronic `brake()` to register at the junction checkpoint[cite: 109, 112, 114].

#### 3. State Engine & Decision Tree Mapping (`thinker()`)
[cite_start]The main firmware orchestrates global path planning via an explicitly designed nested state engine called `thinker()`[cite: 175].
* [cite_start]Manages positions using variables for **Previous Position (`ppos`)**, **Current Position (`cpos`)**, and **Next Position (`npos`)**[cite: 194].
* [cite_start]A dedicated evaluation routine, `uturnck()`, analyzes structural vectors prior to motion execution to test if a 180-degree orientation flip on the spot is required before embarking on the next shortest-path switch case[cite: 118, 178].

#### 4. Asynchronous Wireless Server Telemetry
[cite_start]Real-time remote mapping coordinates continuously over local network protocols using the CC3100 wireless chipset[cite: 156].
* [cite_start]Configures network handshakes using persistent blocking logic to ensure structural stability (`WL_CONNECTED`)[cite: 189].
* [cite_start]Encapsulates data into direct payload methods (`POST /api/arrived/...`) to register at specific track nodes without causing network crashes or data latency[cite: 161, 162].
* [cite_start]Parses text-based server strings, catching non-`200 OK` status codes with automated retry fallbacks, and extracting instructions to safely flag a concluded route run when payload limits hit string terminators[cite: 168, 170, 172].

#### 5. Proportional Distance Braking & Parking
[cite_start]The reverse mechanical sub-routine leverages raw input bounds from the rear analog distance sensor[cite: 137, 138]. [cite_start]The proximity controller utilizes dynamic deceleration variables to execute safety parking sequences[cite: 144]:
* Regulates torque profiles in reverse proportional to proximity data: 
  $$\text{reverseSpeed} = 100 - \frac{\text{rearSensor}}{10}$$
* [cite_start]Implements a mechanical threshold floor of `30` PWM to prevent the motors from stalling due to friction constraints, completely disabling drive operations once physical alignment steps are finalized[cite: 145, 150].

---

### System Demonstration
To see the mechatronics assembly executing its live track routines during testing, watch the video demonstration below:

{{< youtube id="dQw4w9WgXcQ" >}}
