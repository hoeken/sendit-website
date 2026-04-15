---
layout: default
title: API & Integrations
parent: Software
nav_order: 3
---

# API & Integrations

## MQTT

SendIt publishes each channel's data as sub-topics under: `yarrboard/{hostname}/adc/{key}/`

where `{hostname}` is your board's configured hostname (default: `sendit`) and `{key}` is the channel key set in **Settings → ADC Channels**.

Published sub-topics per channel:

| Sub-topic | Description |
|---|---|
| `.../value` | Processed value based on the selected Input Type (e.g., mA, volts, ohms) |
| `.../calibrated_value` | Final calibrated value (only published if a calibration table is configured) |
| `.../adc_voltage` | Raw voltage measured at the ADC input |
| `.../adc_raw` | Raw ADC count |

### Home Assistant

To use SendIt with Home Assistant, follow these steps:

* Install the **Mosquitto Broker** add-on in Home Assistant (or configure an external MQTT broker under **Settings → Devices & Services → MQTT**).
* In SendIt, go to **Settings → Integrations** and enable both **MQTT** and **Home Assistant** features.
* Optionally, go to **Settings → ADC Channels** and select a **Home Assistant Device Class** for each channel to control units and icons in HA.
* In Home Assistant, the SendIt board and its channels should appear automatically under **Settings → Devices & Services → MQTT**.

## Raw API

The protocol for communicating with Yarrboard is entirely based on JSON messages. Each request to the server should be a single JSON object, and the server will respond with a JSON object.

The protocol works over the following transport layers:

* HTTP API
* Websockets
* USB Serial
* MQTT

Since SendIt is not interactive, the most useful command is `get_update` to get the latest readings:

```javascript
{"cmd": "get_update"}
```

Each channel in the response includes:

| Field | Description |
|---|---|
| `id` | Channel number (0–7) |
| `key` | Configured channel key |
| `value` | Processed value based on Input Type (e.g., mA, volts, ohms) |
| `calibrated_value` | Final calibrated value (only present if a calibration table is configured) |
| `adc_voltage` | Raw voltage measured at the ADC input |
| `adc_raw` | Raw ADC count |

Visit the [YarrboardFramework documentation](https://github.com/hoeken/YarrboardFramework#protocol) page for more details on the underlying protocol.

## SignalK

SignalK integration is currently in development. In the meantime, you can bridge MQTT to SignalK using a Node-RED flow:

1. Subscribe to your SendIt MQTT topics (e.g., `yarrboard/sendit/adc/water_tank/value`)
1. Apply any unit conversions needed
1. Publish the result to the appropriate SignalK path

This works reliably today and gives you full control over path naming and unit mapping.