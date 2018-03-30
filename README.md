# Bluetooth GATT Server Sample

This application demonstrates accessing the `BluetoothGattServer` Android API
from within an Android Things application. The sample application advertises
the [Current Time Service](https://www.bluetooth.com/specifications/gatt/services),
and implements the server role of the GATT
[Time Profile](https://www.bluetooth.com/specifications/adopted-specifications).

## Pre-requisites

- Android Things compatible board
- Android device running Android 4.3 (API 18) or later
- Android Studio 2.2+

## Getting Started

1.  Import the project using Android Studio and deploy it to your board.
    The sample will automatically enable the Bluetooth radio, start a GATT
    server, and begin advertising the Current Time Service.
2.  Install the [Android BluetoothLeGatt client](https://github.com/googlesamples/android-BluetoothLeGatt)
    sample on your Android mobile device.
3.  Use the client app to scan and connect to your Android Things board, and
    inspect the services and characteristics exposed by the GATT server.
5.  Read the value of the **Current Time** characteristic (`0x2A2B`).
6.  Register for notifications on the **Current Time** characteristic. The client
    receives an update once per minute with the latest time.
7.  Manually [set the time](#setting-the-time) on your board. The time change
    triggers a notification to the client.

## Setting the Time

You can set the system clock date/time manually on your Android Things board
with the `date` shell command over [ADB](https://developer.android.com/studio/command-line/adb.html).
By default, the command accepts a new date in the `MMddHHmmYYYY.ss` format:

```
# Reboot ADB into root mode
$ adb root

# Set the date to 2017/12/31 12:00:00
$ adb shell date 123112002017.00
```

## Setting the Time Zone

You can set the system time zone manually by updating the `persist.sys.timezone`
system property over [ADB](https://developer.android.com/studio/command-line/adb.html).

```
# Reboot ADB into root mode
$ adb root

# Set the time zone to US Mountain Time
$ adb shell setprop persist.sys.timezone "America/Denver"
```

## License

Copyright 2017 The Android Open Source Project, Inc.

Licensed to the Apache Software Foundation (ASF) under one or more contributor
license agreements.  See the NOTICE file distributed with this work for
additional information regarding copyright ownership.  The ASF licenses this
file to you under the Apache License, Version 2.0 (the "License"); you may not
use this file except in compliance with the License.  You may obtain a copy of
the License at

  http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.  See the
License for the specific language governing permissions and limitations under
the License.
