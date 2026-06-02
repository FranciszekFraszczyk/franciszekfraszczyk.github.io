---
title: "Mobile Robot"
description: "A dual-axis robotic rover utilizing computer vision and PID loops for precise obstacle avoidance."
date: 2026-06-02
showAuthor: false

# Adding 'featured: true' highlights this project at the top of lists!
featured: true

# This links a background preview image to the card on the grid
thumbnail: "img/rover-thumbnail.jpg"
---

### Project Overview
Write a 2-3 sentence high-level summary of what this project actually is, the problem it solves, and its ultimate performance success.

### Technical Engineering Stack
* **Microcontrollers:** Arduino Mega 2560 / Raspberry Pi 4
* **Sensors:** Ultrasonic Transducers, Solid-State LiDAR, 6-DoF IMU
* **Actuators:** High-Torque DC Geared Motors with Quadrature Encoders
* **Languages & Frameworks:** C++, Python, ROS2 (Robot Operating System)

---

### Core Subsystems & Implementation

#### 1. Sensor Fusion & Navigation
Explain your design choices here. For example: *We integrated an IMU with wheel encoder telemetry using an Extended Kalman Filter (EKF) to ensure highly accurate odometry estimation, even on loose terrain.*

#### 2. Computer Vision Integration
Detail your software layer: *The Raspberry Pi runs an OpenCV pipeline capturing a 1080p video stream, filtering out noise in the HSV color space to track specific geometric shapes.*

---

### System Demonstration
To see the mechatronics assembly executing its live path-planning routine, watch the deployment run below:

{{< youtube id="dQw4w9WgXcQ" >}}
