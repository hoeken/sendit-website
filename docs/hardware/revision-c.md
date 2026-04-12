---
layout: default
title: Revision C
parent: Hardware
nav_order: 1
---

# SendIt Revision C

## Features

<div class="d-none d-md-block float-right ml-3 mb-3" style="width: 300px;"><a href="/assets/SendIt Rev C Assembled.jpg"><img src="/assets/SendIt Rev C Assembled.jpg" alt="SendIt Board Assembled" class="img-fluid"></a></div>
<div class="d-block d-md-none mb-3"><a href="/assets/SendIt Rev C Assembled.jpg"><img src="/assets/SendIt Rev C Assembled.jpg" alt="SendIt Board Assembled" class="img-fluid w-100"></a></div>

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

<div class="d-none d-md-block float-right ml-3 mb-3" style="width: 300px;"><a href="/assets/SendIt Rev C Voltage Select.jpg"><img src="/assets/SendIt Rev C Voltage Select.jpg" alt="SendIt Board Voltage Select" class="img-fluid"></a></div>
<div class="d-block d-md-none mb-3"><a href="/assets/SendIt Rev C Voltage Select.jpg"><img src="/assets/SendIt Rev C Voltage Select.jpg" alt="SendIt Board Voltage Select" class="img-fluid w-100"></a></div>

SendIt has 4 different supply voltages available that can be selected by using a jumper shunt on a per-channel basis:

- 24v (max 150mA total) usually for powering 4-20mA sensors
- 5v (max 500mA total)
- 3.3v (max 500mA total)
- External Supply (supplied via connector)

Each channel has a 30mA resettable fuse on the supply voltage.

## Measurement Options

<div class="d-none d-md-block float-right ml-3 mb-3" style="width: 300px;"><a href="/assets/SendIt Rev C Measurement Select.jpg"><img src="/assets/SendIt Rev C Measurement Select.jpg" alt="SendIt Board Measurement Select" class="img-fluid"></a></div>
<div class="d-block d-md-none mb-3"><a href="/assets/SendIt Rev C Measurement Select.jpg"><img src="/assets/SendIt Rev C Measurement Select.jpg" alt="SendIt Board Measurement Select" class="img-fluid w-100"></a></div>

SendIt has 5 different measurement types that can be selected by using jumper shunts to configure the board on a per-channel basis.

Revision C has the following built-in hardware measurement circuits:

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
1. Select **420** as your measurement type.
1. Wire your sender with the positive/supply wire to +VE and the negative/return wire to SIGNAL

{: .note }
If you need to need to power a large number of 4-20mA sensors, it is best to provide an external power supply and select that as the supply voltage.  The 24v regulator on the board is somewhat small and may overheat.

### 240-30 ohm / 0-180 ohm / 0-190 ohm Senders

Resistive senders are commonly used as tank level sensors for water and fuel tanks.  You will need an external 150 ohm resistor to build this circuit.  Larger resistor values also work, but reduce the accuracy slightly.  1k is probably about the maximum you would want to use.  Use resistors with a tolerance of 1% or better and a minimum wattage of 1/10W (100mW)

1. Select **3.3v** as your voltage
1. Wire your resistor between **+VOLTAGE** and **SIGNAL**
1. Wire your sender between **SIGNAL** and **GROUND**

### Positive Switching

1. Select either **3.3v** or **24v** as your voltage
1. Select either **5.0v** or **32v** as your measurement type, depending on the voltage that is being switched.
1. Wire your switch between **+VOLTAGE** and **SIGNAL**

### Negative Switching

1. Select **10K** as your measurement type.
1. Wire your switch between **SIGNAL** and **GND**

### 0-32v Input

1. Select **32v** as your measurement type
1. Wire your voltage to **SIGNAL** and ground to **GROUND**

### 0-5v Input

1. Select **5v** as your measurement type
1. Wire your voltage to **SIGNAL** and ground to **GROUND**

### Thermistor

1. Select **10K** as your measurement type
1. Wire your thermistor between **SIGNAL** and **GROUND**

### Custom Input Voltage

If you have a nonstandard input voltage that doesn't fit the 0-5v range, or the 0-32v range, you can use a custom voltage divider to translate your voltage into a range suitable for SendIt.

1. Select your resistors using the [TI Voltage Divider Calculator](http://ti.com/download/kbase/volt/volt_div3.htm)
  - **Input Voltage** - your maximum input voltage
  - **Desired Output Voltage** - 2.048
  - **Resistor Sequence** - E24 (more common)
  - **Resistor Scale** - 10000
1. Set your measurement type to **RAW**
1. Wire up your custom voltage divider.  Use 1% resistors for best accuracy.
  - **R1** between **YOUR SENSOR** and **SIGNAL**
  - **R2** between **SIGNAL** and **GROUND**
  - **+VOLTAGE** and **GROUND** to your sensor as appropriate.

### Custom Circuit

You can connect your own analog signal directly to the ADC pin of the ADS1115 if needed.  The ADS1115 is configured to measure from 0-2.048v by default.  Do not exceed 3.3v on this pin, or you risk damaging the board.

1. Select **RAW** as your measurement type
1. Wire your sensor as needed.
1. If you have a higher voltage, consider using the 0-5v circuit instead.

## Source Files

* [SendIt Github Repository](https://github.com/hoeken/sendit)
* [SendIt Rev C Schematic](https://github.com/hoeken/sendit/blob/main/schematics/SendIt%20Rev%20C%20Schematic.pdf)
* [3D Printable Case](https://github.com/hoeken/sendit/blob/main/cases/SendIt%20Rev%20B%20Case.step)

## Software Settings

After you have selected your hardware settings and wired up your sensors, you need to [set the appropriate settings](/docs/software/configuration) in software to let SendIt know how to interpret the readings.

# Manufacturing

If you would like to manufacture your own boards, follow the instructions below:

## Kicad File Preparation

- Install the Kicad **Fabrication Toolkit** plugin.
- From the PCB Editor, open **Tools -> External Plugins -> Fabrication Toolkit**
- Click **Generate** to create the production files.
- Upload the **{board_name}.zip** file in the first step of the JLC ordering process
- **{board_name}_bom.csv** file is the Bill of Materials for PCBA
- **{board_name}_positions.csv** file is the Component Placement file for PCBA

## JLCPCB Ordering Options

If no option is specified below, use the default options provided by JLCPCB.

### PCB

* PCB Color: Blue
* Surface Finish: ENIG

### PCB Assembly

* Depanel Boards: YES
* PCBA Remark - attach image below
* PCBA Remark - add the text below

```
After production, insert the following parts:
INPUT6 - LCSC C5188249
INPUT1-INPUT5, INPUT7-INPUT9 - LCSC C5188250
```

![SendIt Manufacturing Instructions]({{ 'assets/SendIt Rev C Manufacturing.png' | relative_url }})