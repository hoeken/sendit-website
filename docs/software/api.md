---
layout: default
title: API & Integrations
parent: Software
nav_order: 3
---

# API & Integrations

## MQTT
Publishes all available information under topic: `yarrboard/sendit/adc/{id|key}`

- Raw reading / voltage
- Calibrated reading

### Home Assistant

To use SendIt with Home Assistant, follow these steps:

* Install the Mosquitto Broker (MQTT server) app in Home Assistant.
* Enable MQTT discovery in Home Assistant
* In SendIt, enable MQTT and the Home Assistant features
* In SendIt, select a Home Assistant sensor type for each channel (optional)
* In Home Assistant, it should show the discovered SendIt board and each channel

## Raw API

The protocol for communicating with Yarrboard is entirely based on JSON messages. Each request to the server should be a single JSON object, and the server will respond with a JSON object.

The protocol works over the following transport layers:

* HTTP API
* Websockets
* USB Serial
* MQTT

Since SendIt is not interactive, the most useful command is 'get_update' to get the latest readings:

```javascript
{"cmd": "get_update"}
```

Visit the [YarrboardFramework documentation](https://github.com/hoeken/YarrboardFramework#protocol) page for more details on the underlying protocol.

## SignalK

SignalK support is not finished yet, so is currently best to setup a NodeRED flow to subscribe to a MQTT topic, do any unit conversions needed, and then publish that to a SignalK path.