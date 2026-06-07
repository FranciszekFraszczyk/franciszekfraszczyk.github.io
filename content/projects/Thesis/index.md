---
title: "Physical AI Predictive Maintenance: Monitoring Industrial Motors Using Distributed Edge Sensors"
description: "An edge-computed anomaly detection platform combining mechanical vibrational acoustics with embedded TinyML neural inferences for real-time industrial fault classification."
date: 2026-03-18
showAuthor: false
featured: true
thumbnail: "featured.jpg"
---

### Project Overview

<div style="text-align: justify;">
Developed as the core focus of my Master of Engineering (MEng) thesis at Dublin City University, this project presents the end-to-end design, implementation, and empirical validation of an asset monitoring framework utilizing <strong>Physical AI</strong>. The architecture fuses raw mechanical physics domain knowledge with constrained, real-time edge computing. By migrating signal processing and machine learning models directly onto hardware nodes, the platform extracts high-frequency structural acoustic parameters to predict mechanical abnormalities before destructive degradation occurs.
</div>

### Technical Engineering Stack

<div style="text-align: justify;">

* **Embedded Hardware Layer:** High-Speed Microcontrollers with Dedicated Signal Processing Layouts
* **Machine Learning & Inference:** TinyML Neural Network Inferences & Vector Quantization Pipeline
* **Signal Core Architecture:** Fast Fourier Transforms (FFT), Acoustic Feature Extraction, and Bandpass Filtering Loops
* **Development Environments:** PlatformIO Ecosystem & Optimized Python Core Implementations
* **Telemetry & Visualizations:** Low-latency Multi-Core Hard Real-Time Task Framework paired with Local Bus Pipelines

</div>

---

### Core Systems & Architecture

#### 1. Real-Time Edge Data Collection Pipeline

<div style="text-align: justify;">
The physical intelligence layer begins with real-time structural boundary signal tracking. High-frequency acoustic vibrations and structural stress waveforms are ingested via dedicated analogue conditioning topologies. The data stream is dynamically handled on-device to isolate steady-state signals from ambient machinery noise floor patterns.
</div>

<div style="text-align: center; margin: 20px 0;">
  <img src="sensor_hardware.jpg" alt="Embedded Sensor Node Deployment" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 1: Custom edge monitoring hardware integrated directly onto the target testbed chassis.</p>
</div>

#### 2. Physical AI Feature Extraction & On-Device Processing

<div style="text-align: justify;">
To circumvent massive telemetry transmission overloads, raw time-domain vectors are immediate processed in-situ. The controller performs rapid Fast Fourier Transforms (FFTs) to translate raw kinetic acceleration and shock vectors into frequency-bin signatures. Peak component thresholds, spectral energy trends, and harmonic coefficients are compiled into feature frames, preparing the data for localized diagnostic checking.
</div>

<div style="text-align: center; margin: 20px 0;">
  <img src="signal_processing.jpg" alt="FFT Frequency Domain Spectrum Analysis" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 2: Spectral energy mappings isolating unique resonance shifts associated with fatigue fractures and early bearing anomalies.</p>
</div>

#### 3. Constrained TinyML Classification Engine

<div style="text-align: justify;">
At the heart of the predictive matrix is an optimized TinyML neural inference engine working directly on the microcontroller core. The algorithm references mathematical multi-layer classification rules to separate structural signatures into strict health brackets (e.g., Stable, Early Degraded, Critical Fault). This setup achieves an incredible reduction in power draw and localized decision latency, running deterministically without depending on cloud servers.
</div>

<div style="text-align: center; margin: 20px 0;">
  <img src="neural_network_architecture.jpg" alt="TinyML Classification Engine Structure" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 3: Topology layout of the constrained artificial neural network deployed onto the physical AI node.</p>
</div>

#### 4. Hard Real-Time Resource Scheduling & Telemetry

<div style="text-align: justify;">
To prevent data drops during intense mathematical processing routines, the system utilizes a strict hard real-time scheduling loop. High-priority tasks capture incoming sensor waves, while background routines manage the neural inference loops and package the resulting classification metrics. These summarized fault packets are then pushed via low-latency serial or wireless bus configurations straight to centralized industrial control dashboards.
</div>

<div style="text-align: center; margin: 20px 0;">
  <img src="dashboard_metrics.jpg" alt="Predictive Analytics Dashboard UI" style="max-width: 100%; height: auto; border-radius: 4px;">
  <p style="font-size: 0.9rem; font-style: italic; color: #666; margin-top: 8px;">Figure 4: Real-time telemetry monitoring panel tracking machine lifetime predictions and structural degradation gradients.</p>
</div>

---

### Platform System Demonstrations

To observe the real-time classification response speeds, feature-space transitions, and physical validation runs under active fatigue conditions, view the system walkthrough sequences below:

#### Edge Inference & Fault Injection Testing
{{< youtube id="YOUR_VIDEO_ID_HERE_1" >}}

#### Analytical Calibration & Signal Processing Run
{{< youtube id="YOUR_VIDEO_ID_HERE_2" >}}
