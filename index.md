---
layout: default
title: Overview
nav_order: 1
---

# SendIt - ADC Input Multitool

<a href="/docs/hardware/revision-c"><img src="/assets/SendIt Rev C Assembled.jpg" alt="SendIt Board Assembled" class="img-main"></a>

SendIt is an open-hardware, open-firmware controller designed as a multi use tool for handling various inputs with a focus on DIY marine usage.  It runs on the Yarrboard Framework and provides a clean web UI for configuration, and multiple different APIs for accessing your data.

Built on the ESP32-S3, SendIt has 8 channels of 16-bit ADC with configurable input circuits.  This board can handle these types of inputs:

* 4-20ma Transducers/Senders
* 240-30 ohm / 0-180 ohm senders
* Positive Switching
* Negative Switching
* 0-32v Input
* 0-5v Input
* 0-10k ohm resistance
* Thermistors
* Raw ADC Input

## User Interface

![SendIt - Typical interface](/assets/sendit ui.png)

- Local HTML5 web interface served from the ESP32  
- Fast, mobile-friendly design  
- Works on phones, laptops, and supported MFDs  
- Real-time dashboard with sensor readings
- Web based UI config - no manually editing config files  

## Integrations
- MQTT
- SignalK 
- Home Assistant
- HTTP/REST endpoints  
- WebSocket real-time control