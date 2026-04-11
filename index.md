---
layout: default
title: Overview
nav_order: 1
---

# SendIt - ADC Input Multitool

## Hardware

<a href="assets/SendIt Rev C Vertical.jpg"><img src="assets/SendIt Rev C Vertical.jpg" alt="SendIt Rev C" style="float: right; margin: 0 0 1em 1.5em; width: 180px;"></a>

- 8 channel ADC input (ADS1115)
- 5 input type circuits, selectable by jumper:
  - 4-20ma sensor
  - 0-30v input
  - 0-5v input
  - 10k pullup
  - Raw input
- Per-channel supply voltage:
  - 24v
  - 5v
  - 3.3v
  - External Power
- Built-in 24v power supply for 4-20ma sensors
- Powered by USB or 12-30v external input
- QWIIC and GPIO expansion port

## User Interface
- Local HTML5 web interface served directly from the ESP32  
- Fast, mobile-friendly design  
- Works on phones, laptops, and supported MFDs  
- Real-time dashboard with sensor readings
- Full configuration editor UI - no editing config files  

## Integrations
- MQTT publishing
- SignalK 
- Home Assistant
- HTTP/REST endpoints  
- WebSocket real-time control

### Example User Interface
