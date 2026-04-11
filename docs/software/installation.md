---
layout: default
title: Firmware Installation
parent: Software
nav_order: 1
---

# Firmware Installation

<a href="assets/provisioning.png"><img src="assets/provisioning.png" alt="Provisioning UI" style="float: right; margin: 0 0 1em 1.5em; width: 300px;"></a>

## Upload Firmware

If your board does not come pre-programmed, you will need to upload the firmware.

1. Open the [Firmware Helper](https://firmware.sendit.yarrboard.com) page
1. Select your board revision
1. Select your firmware version
1. Click Install Firwmare
1. Select your serial port, click upload

## WiFi Provisioning

1. Open the [Firmware Helper](https://firmware.sendit.yarrboard.com) page
1. Select either `Configure via BLE` or `Configure via Serial`
1. Enter your WiFi credentials
1. Open browser to [http://sendit.local](http://sendit.local)

## Firmware Update Methods

* Update the firmware using OTA from the web interface
* Use the Firmware Helper linked above to choose a specific version
* Compile from source using instructions below

## Development / Building From Source

1. Clone the [firmware repository](https://github.com/hoeken/sendit-firmware)
1. Run ```npm install``` in the repository to get some dev tools
1. Plug your computer into the board
1. Open the repository in VSCode
1. Install the Platformio plugin if needed
1. At the bottom, select your board from the build environments
1. Build and/or upload firmware with the arrow in the upper right.

### ArduinoOTA

This allows you to upload new firmware over wifi from VSCode.

1. Enable Arduino OTA in Settings -> Miscellaneous on the board
1. Edit platformio.ini and add this to the bottom of your desired board [env:] section

```
; OTA Upload Config, auth password is your admin password
upload_protocol = espota
upload_port = sendit.local
upload_flags = 
 	--auth=admin
 	--port=3232
```