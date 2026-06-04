---
title: "Autonomous Mobile Robot"
description: "An autonomous line-tracking mobot featuring embedded navigation, synchronous server communication, and a custom web remote-control interface."
date: 2024-02-22
showAuthor: false
featured: true

# Links the local image package asset seamlessly 
thumbnail: "featured.jpg"
---

### Project Overview
Developed as part of the EE303 Mobile Robotics module at Dublin City University, this project involved the design, manufacturing, and firmware optimization of an autonomous mobile robot ("Mobot"). The system was engineered to autonomously navigate a physical track, cross marked intersection checkpoints, and perform precision parking operations against track boundary structures. When the robot reached its destination, the car's position would update on the server and the next destination point would be sent to the robot.

### Technical Engineering Stack
* **Microcontroller Platform:** Texas Instruments MSP432 LaunchPad
* **Wireless Transceiver Module:** CC3100 SimpleLink Wi-Fi Network Processor
* **Motor Control System:** DRV8835 Dual Motor Driver Carrier (Dual H-Bridge IC)
* **Sensor Arrays:** Front-mounted 5-Channel Infrared (IR) Reflectance Sensor PCB , Rear Analog Proximity Sensor
* **Power Subsystem:** 9.6V battery pack paired with a DC-to-DC buck converter
* **Firmware Environment:** C/C++ (Energia IDE Framework)
* **Web Telemetry Stack:** Asynchronous JavaScript and XML (AJAX), JavaScript, and Custom CSS (for the remote control interface framework)

---

### Core Subsystems & Implementation

#### 1. Sensor Calibration & Smoothing Framework (`Sense()`)
To limit signal bounce and prevent erratic over-steering from high-frequency analog line tracking spikes, a low-pass software smoothing function was implemented. The sensor suite captures data streams in the range of `50-150` for light/white surfaces and `600-900` for dark/black boundaries:
* Reads values natively via five concurrent `analogRead()` mapping pipelines.
* Generates a moving average across every ten raw input streams using a dedicated loop matrix to maintain stable tracking data arrays.
* Integrated a `1k Ohm` resistor integrated circuit (IC) to isolate sensory boards from voltage surges.

#### 2. Dual-Axis Line Tracking Logic
The navigation script uses the data arrays to dynamically regulate the dual DC motors. By configuring a threshold limit of `150` to declare a valid track intersection, the bot actively calculates spatial adjustments.
* **Directional Adjustments:** Micro-steering corrections execute on the fly; triggering the interior left sensor commands a localized left turn, while triggering the interior right sensor commands a right turn.
* **Horizontal Stop Points:** Whenever the outer boundary limits (Sensors 1 and 5) simultaneously identify a white horizontal line crossbar, the firmware triggers a complete zero PWM electronic `brake()` to register at the junction checkpoint.

#### 3. State Engine & Decision Tree Mapping
The main firmware orchestrates global path planning via an explicitly designed nested state engine.
* Manages positions using variables for **Previous Position (`ppos`)**, **Current Position (`cpos`)**, and **Next Position (`npos`)**.
* A dedicated evaluation routine, `uturnck()`, analyzes structural vectors prior to motion execution to test if a 180-degree orientation flip on the spot is required before embarking on the next shortest-path switch case.

#### 4. Asynchronous Wireless Server Telemetry
Real-time remote mapping coordinates continuously over local network protocols using the CC3100 wireless chipset.
* Configures network handshakes using persistent blocking logic to ensure structural stability (`WL_CONNECTED`).
* Encapsulates data into direct payload methods (`POST /api/arrived/...`) to register at specific track nodes without causing network crashes or data latency.
* Parses text-based server strings, catching non-`200 OK` status codes with automated retry fallbacks, and extracting instructions to safely flag a concluded route run when payload limits hit string terminators.

#### 5. Proportional Distance Braking & Parking
The reverse mechanical sub-routine leverages raw input bounds from the rear analog distance sensor. The proximity controller utilizes dynamic deceleration variables to execute safety parking sequences:
* Regulates torque profiles in reverse proportional to proximity data: 
  $$\text{reverseSpeed} = 100 - \frac{\text{rearSensor}}{10}$$
* Implements a mechanical threshold floor of `30` PWM to prevent the motors from stalling due to friction constraints, completely disabling drive operations once physical alignment steps are finalized.

---

### System Demonstration
To see the mechatronics assembly executing its live track routines during testing, watch the video demonstration below:

{{< youtube id="dQw4w9WgXcQ" >}}
