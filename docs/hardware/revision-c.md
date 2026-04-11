---
layout: default
title: Revision C
parent: Hardware
nav_order: 1
---

# SendIt Revision C

## Features
- ESP32-S3 module with WiFi and USB-C  
- 12–30 V DC input with onboard power regulation  
- Can be powered by USB C or external power input
- 8 x 16-bit ADC channels (ADS1115)
- 5 input type circuits, selectable by jumper
- Per-channel supply voltage: External / 24v / 5v / 3.3v
- 30mA resettable fuse on sensor supply
- Built-in 24v power supply for 4-20ma sensors
- Powered by USB or 12-30v external input
- I²C expansion (QWIIC connector)
- Unused I/O broken out as 2.54mm pin headers

## Hardware Pinout

[![SendIt Rev C Pinout](/assets/Sendit Rev C Pinout.png)](/assets/Sendit Rev C Pinout.pdf)

## ADC Input Channel Schematic

[![SendIt Rev C ADC Channel](/assets/SendIt ADC Channel - Rev C.png)](/assets/SendIt ADC Channel - Rev C.pdf)

## Voltage Options

SendIt has 4 different supply voltages available that can be selected by using a jumper shunt on a per-channel basis:

- 24v (max 150mA total) usually for powering 4-20mA sensors
- 5v (max 500mA total)
- 3.3v (max 500mA total)
- External Supply (supplied via connector)

Each channel has a 30mA resettable fuse on the supply voltage.

## Measurement Options

SendIt has 5 different measurement types that can be selected by using jumper shunts to configure the board on a per-channel basis.

Revision C supports the following hardware measurement types:

- 4-20ma sensors
- 0-32v input
- Raw ADC input
- 10k pullup to 3.3v
- 0-5v input

{: .warning }
You must install jumpers on both top and bottom measurement settings.  Make sure you have selected the same setting for both top and bottom.

### 4-20ma Transducers / Senders

4-20mA senders are very common sensors for a variety of applications.

1. Select an appropriate voltage for your sender.  24v is fairly standard.
1. Select `420` as your measurement type.
1. Wire your sender with the positive/supply wire to +VE and the negative/return wire to SIGNAL

{: .note }
If you need to need to power a large number of 4-20mA sensors, it is best to provide an external power supply and select that as the supply voltage.  The 24v regulator on the board is somewhat small and may overheat.

### 240-30 ohm / 0-180 ohm / 0-190 ohm Senders

Resistive senders are commonly used as tank level sensors for water and fuel tanks.  You will need an external 150 ohm resistor to build this circuit.  Larger resistor values also work, but reduce the accuracy slightly.  1k is probably about the maximum you would want to use.

1. Select '3.3v' as your voltage
1. Wire your resistor between +VOLAGE and SIGNAL
1. Wire your sender between SIGNAL and GROUND

### Positive Switching

1. Select either `3.3v` or `24v` as your voltage
1. Select either `5.0v` or `32v` as your measurement type, depending on the voltage that is being switched.
1. Wire your switch between +VOLTAGE and SIGNAL

### Negative Switching

1. Select `10K` as your measurement type.
1. Wire your switch between SIGNAL and GND

### 0-32v Input

1. Select `32v` as your measurement type
1. Wire your voltage to SIGNAL and ground to GROUND

### 0-5v Input

1. Select `5v` as your measurement type
1. Wire your voltage to SIGNAL and ground to GROUND

### Thermistor

1. Select `10K` as your measurement type
1. Wire your thermistor between SIGNAL and GROUND

### Custom Circuit

You can connect directly to the ADC pin of the ADS1115 with your own custom circuit if needed.  The ADS1115 is configured to measure from 0-2.048v.  Do not exceed 3.3v on this pin, or you risk damaging the board.

1. Select 'RAW' as your measurement type
1. Wire your sensor as needed.

## Software Settings

After you have selected your hardware settings and wired up your sensors, you need to [set the appropriate settings]({{ '/docs/software/operation' | relative_url }}) in software to let SendIt know how to interpret the readings.