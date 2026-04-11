---
layout: default
title: API & Integrations
parent: Software
nav_order: 3
---

# API & Integrations

## MQTT
Publishes all available information:
- Raw reading  
- Calibrated reading
- etc.

Under topic: `yarrboard/sendit/*`

### Home Assistant

To use SendIt with Home Assistant, follow these steps:

* Install the Mosquitto Broker (MQTT server) app in Home Assistant.
* Enable MQTT discovery in Home Assistant
* In SendIt, enable MQTT and the Home Assistant features
* In Home Assistant, it should show the discovered SendIt board and each channel

**TODO: add link to dashboard YAML here**

## Raw API

The protocol for communicating with Yarrboard is entirely based on JSON messages. Each request to the server should be a single JSON object, and the server will respond with a JSON object.

The protocol works over the following transport layers:

* HTTP API
* Websockets
* USB Serial
* MQTT

Since SendIt is not interactive, the most useful command is 'get_update' to get the latest readings:

```
{"cmd": "get_update"}
```

Visit the [YarrboardFramework documentation](https://github.com/hoeken/YarrboardFramework#protocol) page for more details on the underlying protocol.

## SignalK

//todo: signalk support isnt really setup yet.