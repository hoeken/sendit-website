---
layout: default
title: Software
nav_order: 3
has_children: true
---

# Software

SendIt firmware is fully open source and licensed under the **GPLv3** license.

View the source on [github](https://github.com/hoeken/sendit-firmware).

## Firmware Overview

SendIt firmware runs on the [YarrboardFramework](https://github.com/hoeken/YarrboardFramework), which provides:
- Individual configuration for each of the 8 ADC channels
- Web-based configuration UI — no manual file editing required
- Multiple integration options: MQTT, Home Assistant, SignalK, HTTP, and WebSockets

To get started, follow the steps below in order:
1. [Firmware Installation]({{ '/docs/software/installation' | relative_url }}) — flash firmware and connect to WiFi
2. [Configuration]({{ '/docs/software/configuration' | relative_url }}) — set up your channels and calibrate sensors
3. [API & Integrations]({{ '/docs/software/api' | relative_url }}) — connect to MQTT, Home Assistant, or SignalK