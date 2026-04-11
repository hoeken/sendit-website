---
layout: default
title: Overview
nav_order: 1
---

# SendIt - ADC Input Multitool

<a href="assets/SendIt Rev C Vertical.jpg"><img src="assets/SendIt Rev C Vertical.jpg" alt="SendIt Rev C" style="float: right; margin: 0 0 1em 1.5em; width: 200px;"></a>

SendIt is an open-hardware, open-firmware controller designed as a multi use tool for handling various inputs with a focus on DIY marine usage.  It runs on the Yarrboard Framework and provides a clean web UI for configuration, and multiple different APIs for accessing your data.

Built on the **ESP32-S3**, SendIt has 8 channels of 16-bit ADC with 5 different types of configurable input circuits.  With this board, each channel can be individually configured to handle these types of inputs:

* **4-20ma Transducers/Senders:**
* **Positive Switching:**
* **Negative Switching:**
* **0-32v:**
* **0-10k ohm:**
* **0-5v:**
* **Thermistor:**
* **Raw ADC:**

## User Interface

<a href="assets/sendit ui.png"><img src="assets/sendit ui.png" alt="SendIt UI" style="float: right; margin: 0 0 1em 1.5em; width: 300px;"></a>

- Local HTML5 web interface served from the ESP32  
- Fast, mobile-friendly design  
- Works on phones, laptops, and supported MFDs  
- Real-time dashboard with sensor readings
- Web based UI config - no manually editing config files  

## Integrations
- MQTT publishing
- SignalK 
- Home Assistant
- HTTP/REST endpoints  
- WebSocket real-time control

### Example User Interface
