---
layout: default
title: Configuration
parent: Software
nav_order: 2
---

# Configuration

You can access the firmware at [http://sendit.local](http://sendit.local) ([http://sendit](http://sendit) on Android) or by entering the IP address.  The IP address and hostname are printed out over the serial port at startup.  You should see an interface similar to this:

![SendIt]({{ 'assets/sendit ui.png' | relative_url }})

Go to **Settings -> ADC Channels** page.  There you can edit each channel's configuration.  Most of these settings are self-explanatory, but we will cover some details of each below.  Here is an example water tank sensor configuration:

![SendIt]({{ 'assets/sendit channel config.png' | relative_url }})

### Name / Key / Enabled

Name is what is shown to the user, and key is used for things like MQTT and SignalK paths.  Disable is for turning off unused channels.

### Input Type

Input type determines how SendIt interprets the reading from the ADC:

- **Raw Output** will just give you the voltage directly measured by the ADC.
- **Digital Input** will translate the voltage into HIGH or LOW.  Useful for switches.
- **Thermistor** will translate the voltage into a temperature reading.
- **4-20mA Sensor** will translate the voltage into an amperage reading.
- **0-32v Input** will translate the voltage into the range of 0-32v.
- **0-5v Input** will translate the voltage into the range of 0-5v.
- **10k Pullup** will translate the voltage into an ohm value in a voltage divider where R1 is 10k and R2 is the calculated value.

### Home Assistant Device Class

If you are using Home Assistant Integration, you can select which [device class](https://developers.home-assistant.io/docs/core/entity/sensor/#available-device-classes) it appears as, which allows home assistant to do things like automatically apply units and select icons.

### Running Average Window

High values will smooth out your sensor readings, but make it slightly slower to respond.  Low values will cause it to be faster but possibly more noisy.  Maximum window of 10 seconds.

### Calibration Table

The calibration table allows you to fine-tune your final sensor output.  It also lets you set custom units for the final output such as percentage, liters, or any other unit you like.

Calibration can be as simple as setting a 4-20ma sensor so that 4mA is 0% and 20mA is 100%, or as complicated as calibrating your tank sensor by filling the tank a little bit at a time and measuring the sensor at each liquid level.

It has a built in 'Live Average' so that you can get a stable reading during your calibration process.

**Raw Input** is the reading from the ADC channel and **Calibrated** is the value to output.  SendIt will use linear interpolation between values, so if your sensor is non-linear then you will need multiple data points for a smooth and reliable output.

Here is an example calibration table from a water tank sensor:

![SendIt Calibration Table]({{ 'assets/sendit calibration table.png' | relative_url }})

## Usage

Once SendIt is configured, there is not much interaction needed.  You will want to set up MQTT, SignalK, or some other custom method of polling the sensor values.

[See more on the API & Integrations page]({{ '/docs/software/api' | relative_url }}).