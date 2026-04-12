---
layout: default
title: Hardware
nav_order: 2
has_children: true
---

# Hardware

[![Kicad Layout](/assets/sendit-rev-c layout.png)](/docs/hardware/revision-c)
[![Assembled Board](/assets/SendIt Rev C Horizontal.jpg)](/docs/hardware/revision-c)

## Revisions

- [Revision C]({{ '/docs/hardware/revision-c' | relative_url }}) — latest version, production ready
- **Revision B** — prototype
- **Revision A** — prototype

SendIt hardware is fully open source and licensed under the **Open Hardware License (OHL)** license.

All hardware design files (schematics, layout, gerbers, and BOM) are available on [GitHub](https://github.com/hoeken/sendit).

## Build It Yourself

SendIt is fully open source, so you can order and assemble the PCB yourself. The easiest way to do this is through [JLCPCB](https://jlcpcb.com), which supports ordering fully assembled boards directly from our design files.

[Instructions on how to do that here](/docs/hardware/revision-c.html#manufacturing)

## Buy a Assembled Unit

At some point, we plan on offering assembled PCBs.  If you would like to be notified when they are available, please [enter your email here](https://forms.gle/CyuddCLdqdT9jqcTA).

# Changelog

## REV C

### 🔧 ADC & Analog Front-End
- Switched back to **ADS1115** ADC.
- Removed the **ADC VREF circuit** and added a **solder jumper** for VREF selection.
- Standardized all analog scaling to **2.048 V** reference (instead of 3.3 V).
- Added voltage dividers for **30 V** and **5 V** input ranges.
- Set **4–20 mA shunt resistor** to **100 Ω**.
- Added **pull-up resistors** on ADS1115 ALERT pin.

### ⚡ Power & Regulation
- Added a **buck converter** on the EXT port for **12/24 V → 5 V** to power the ESP32.
  - Includes a jumper to **enable/disable EXT-port power**.
  - EXT port may now be used as **power-only**, **reference-only**, or **both**.
- Added **3.3 V ↔ 5.0 V buffer** for WS2818 LED.
- Switched to **green LEDs** for power indication.
- Removed the **USB-to-serial** and **USB hub** for a simplified ESP32-S3 design.

### 🧩 Connectors & I/O
- Added **QWIIC header**.
- Moved pluggable terminal blocks **down 0.5 mm**.
- Removed jumper for EXT power selection.

### 🧪 Test Points
- Added test points for **3.3 V**, **5.0 V**, **24 V**, **GND**, **SDA**, **SCL**, and others.
- Standardized all test points to **1.5×0.7 mm**.

### 🔊 Piezo & Indicators
- Switched to **passive piezo** and added diode (**Huaneng QMB-09B-03**).

### 🧱 Mechanical & Layout
- Changed upper mounting holes to **SMTSO3080CTJ** hardware.
- Switched to **SMT boot/reset buttons**.
- Removed RTC **clock crystal**.
- Switched boost converter to **MT3608B** for 24 V generation.