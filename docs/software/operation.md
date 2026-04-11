---
layout: default
title: Operation
parent: Software
nav_order: 3
---

# Operation

You can access the firmware at [http://sendit.local](http://sendit.local) ([http://sendit](http://sendit) on Android) or by entering the IP address.  The IP address and hostname are printed out over the serial port at startup.  You should see an interface similar to this:

![SendIt]({{ 'assets/sendit-ui.png' | relative_url }})

## Initial Configuration

Open the web UI and go to the settings page.  There you can edit each channel's configuration.

//todo: add configuration stuff here.

## Usage

Once SendIt is configured, there is not much interaction needed.  You will want to set up either MQTT, SignalK, or some other custom method of polling the sensor values.

From there you can integrate into Home Assistant, Node-RED, or whatever other uses you have for the final sensor data.