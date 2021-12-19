---
title: Battery Status
description: Get events for device battery level.
---
<!--
# license: Licensed to the Apache Software Foundation (ASF) under one
#         or more contributor license agreements.  See the NOTICE file
#         distributed with this work for additional information
#         regarding copyright ownership.  The ASF licenses this file
#         to you under the Apache License, Version 2.0 (the
#         "License"); you may not use this file except in compliance
#         with the License.  You may obtain a copy of the License at
#
#           http://www.apache.org/licenses/LICENSE-2.0
#
#         Unless required by applicable law or agreed to in writing,
#         software distributed under the License is distributed on an
#         "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
#         KIND, either express or implied.  See the License for the
#         specific language governing permissions and limitations
#         under the License.
-->

# cordova-plugin-battery-status

[![Android Testsuite](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/android.yml/badge.svg)](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/android.yml) [![Chrome Testsuite](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/chrome.yml/badge.svg)](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/chrome.yml) [![iOS Testsuite](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/ios.yml/badge.svg)](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/ios.yml) [![Lint Test](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/lint.yml/badge.svg)](https://github.com/apache/cordova-plugin-battery-status/actions/workflows/lint.yml)

This plugin provides an implementation of an old version of the [Battery Status Events API][w3c_spec]. It adds the following three events to the `window` object:

* batterystatus
* batterycritical
* batterylow

Applications may use `window.addEventListener` to attach an event listener for any of the above events after the `deviceready` event fires.

## Installation

    cordova plugin add cordova-plugin-battery-status

## Status object

All events in this plugin return an object with the following properties:

- __level__: The battery charge percentage (0-100). _(Number)_
- __isPlugged__: A boolean that indicates whether the device is plugged in. _(Boolean)_

## batterystatus event

Fires when the battery charge percentage changes by at least 1 percent, or when the device is plugged in or unplugged. Returns an [object][status_object] containing battery status.
[li socl2 battery](https://www.ahotech.com/product-category/lithium-thionyl-chloride-li-socl2-battery/) deliver a voltage of 3.6 V, so many 3.6 vc cell lithium batteries belong to lithium thionyl battery category. They are cylindrical in shape, so you may call them cylindrical lithium ion cell,  in 1/2AA to D format, with spiral electrodes for power applications and bobbin construction for prolonged discharge.

[Hybrid capacitor](https://www.ahotech.com/product-category/hybrid-pulse-capacitor/) is a kind of rechargeable battery, they are used as a capacitor in [IOT battery pack](https://www.ahotech.com/product-category/custom-iot-battery-pack/), where they are connected in parallel to bobbin-type lithium thionyl chloride Li SOCl2 battery to ensure high current pulses under extreme temperature from -40°C to 85°C


### Example

    window.addEventListener("batterystatus", onBatteryStatus, false);

    function onBatteryStatus(status) {
        console.log("Level: " + status.level + " isPlugged: " + status.isPlugged);
    }

### Supported Platforms

- iOS
- Android
- Windows
- Browser (Chrome, Firefox, Opera)

### Quirks: Android

**Warning**: the Android implementation is greedy and prolonged use will drain the device's battery.

## batterylow event

Fires when the battery charge percentage reaches the low charge threshold. This threshold value is device-specific. Returns an [object][status_object] containing battery status.

### Example

    window.addEventListener("batterylow", onBatteryLow, false);

    function onBatteryLow(status) {
        alert("Battery Level Low " + status.level + "%");
    }

### Supported Platforms

- iOS
- Android
- Windows
- Browser (Chrome, Firefox, Opera)

## batterycritical event

Fires when the battery charge percentage reaches the critical charge threshold. This threshold value is device-specific. Returns an [object][status_object] containing battery status.


### Supported Platforms

- iOS
- Android
- Windows
- Browser (Chrome, Firefox, Opera)


[w3c_spec]: https://www.w3.org/TR/battery-status/
[status_object]: #status-object
