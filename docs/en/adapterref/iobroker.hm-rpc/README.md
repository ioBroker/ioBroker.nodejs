---
lastChanged: 09.01.2019
local: true
translatedFrom: de
translatedWarning: If you want to edit this document please delete "translatedFrom" field, elsewise this document will be translated automatically again
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/en/adapterref/iobroker.hm-rpc/README.md
title: HomeMatic RPC
hash: 1O7kQJdss1SQKcqoLSdzCOhUQWxAXD2BjOmS727c/E4=
---
![logo](../../../de/adapterref/iobroker.hm-rpc/media/homematic.png)

# HomeMatic RPC
## Homematic
> Homematic is eQ-3's smart home system that provides comprehensive control of a wide range of features, from scenarios (from simple to complex) in the home or apartment.

&gt; The devices include products for light, roller shutter and heating control, hazard detectors, safety sensors and weather data measurement products. Radio communication simplifies retrofitting. In new buildings wire bus components can be used. <a href="https://www.eq-3.de/produkte/homematic.html" title="Homepage of the manufacturer eQ3">source</a>

## Administration and control of homematic components with ioBroker
To optimally manage and control homematic components with ioBroker, two adapters are required:

### 1. Homematic ReGaHss
This adapter connects to the homematic logic layer "ReGaHSS" (** Re **sidential** Gateway).
It synchronizes real names, system variables, rooms, trades and programs between Homematic and ioBroker.

### 2. Homematic RPC
The **R** emote **P** rocedur **C** all, RPC for short is a technique for realizing interprocess communication. This adapter provides the connection to the communication modules of a homematic central unit (CCU / CCU2 / CCU3 ...). The modules rfd (radio), HMIP-rfd, hs485d (wired), CuxD (additional software for connecting external components such as EnOcean, FS20, etc.) and Homegear (CCU replacement) are supported.

This diagram illustrates the structure and communication interfaces:

![](../../../de/adapterref/iobroker.hm-rpc/media/Homematic_Aufbau.png)

[source](http://www.wikimatic.de/wiki/Datei:Homematic_Aufbau.png)

## Adapter Homematic RPC
This adapter provides the connection to the communication modules of a homematic central unit (CCU / CCU2 / CCU3 ...). An instance of the adapter is responsible for exactly ON modules (rfd, wired, etc.). If several modules are to be supported in parallel, a separate instance must be installed for each module.

The adapter communicates with the corresponding module either via BIN-RPC or XML-RPC. Since an event interface is used, the correct addressing is important. Thus, events are automatically transmitted to the adapter and cyclic polling is not necessary.

In addition, the adapter has the functionality to cyclically monitor the connection to the CCU.

If new devices are taught-in at the CCU, then the adapter must be restarted with the configuration "Initiate devices new (once)". This will transfer the information from the new homematic devices to the adapter.

## Configuration
### Main Settings
### HomeMatic address
IP address of the CCU or host running the Homematic BidCos service.

### HomeMatic Port
The setting of the port depends on the required communication module, is entered automatically when selecting the daemon and should only be changed if the ports deviate from the standard.

By default, the following ports are provided:

| Communication module | Standard port | HTTPS port |
|---------------------|--------------|------------|
| Radios (RFD) | 2001 | 42001 |
| Wired | 2000 | 42000 |
| CUxD | 8701 | \ - |
| Homematic IP | 2010 | 42010 |

### Daemon
CCU / Homematic supports different device types (wired, wireless, HMIP, CUxD). For each type a separate instance must be created.

### Protocol
Two protocols are provided for communication: XML-RPC and BIN-RPC.

* CUxD requires the BIN-RPC protocol; HMIP and RFD the XML-RPC protocol. *

### Synchronize devices again (once)
When the adapter is started for the first time, all devices are read. If changes are later made within the CCU (renaming devices, adding new devices, etc.), activate this selection and restart the adapter with "Save and Close".

### Adapter Address
The pull-down menu selects the IP of the host where the adapter is installed. The selection of "0.0.0.0 Listen to all IPs" and "127.0.0.1" is reserved for special cases.

### Adapter Port
By default, port "0" is set here for the automatic selection of the ioBroker port and should only be changed in exceptional cases.

## Additional settings
### Adapter Callback Address
If ioBroker runs behind a router (for example, in a Docker container), input and output addresses may differ. If the IP of the router is entered here, the problem can be avoided, since then the forwarding to ioBroker is taken over by the router.

### Connection check interval (sec)
At the specified interval, a ping request is sent to the CCU.

### Reconnect interval (sec)
Time after which a new connection attempt is started.

### Do not delete devices
By default, devices are also removed from the object list if they have been learned within the CCU. To keep these devices in the object list, for example because they have only been temporarily removed, this option can be activated.

### Use HTTPS
If this option is activated, a secure connection is established.
Works only with XML-RPC protocol.

### Username and password
When using HTTPS or if the API of the CCU requires authentication, the data must be entered here.

## Instance
![instance](../../../de/adapterref/iobroker.hm-rpc/media/10d34a2bc1518fa34233bdb04219e444.png)

Under *Instances* of the ioBroker you will find the installed instance of the adapter. On the left, the traffic light system visualizes whether the adapter is activated and connected to the CCU.

If you place the mouse pointer on a symbol, you will get detailed information.

## Objects of the adapter
In the Objects area, all values and information transmitted by the CCU to the adapter are displayed in a tree structure.

The objects and values displayed depend on the devices (function and channels) and the structure within the CCU.

The control panel is marked with the ID BidCoS-RF (which includes all virtual keys), devices are created under their serial number and groups are labeled with INT000000 *x*

### Channel 0 (all devices)
This channel is created for each device and contains function data, following a brief overview:

| *Data point* | *Meaning* |
|--------------------------------|--------------------------------------------------------|
| AES_Key | Encrypted activation active / inactive |
| Config (Pending / Pending Alarm) | Pending configuration |
| Dutycycle / Dutycycle Alarm | Airtime Homematic Devices |
| RSSI (Device / Peer) | Radio strength (device \ <-> Central) |
| Low Bat / Low Bat Alarm | low battery charge |
| Sticky unreach / unreach alarm | System message communication error (fault occurred) |
| Unreach / unreach alarm | System message communication error (current state) |

### Channels 1-6
Here, measured values, control and status data are listed; depending on the function of the device different data are displayed. Here is a short excerpt:

| *Function* | *Channel* | *Possible values* |
|-------------------------|---------|-----------------------------------------------------------|
| Sensors | 1 | Temperature, humidity, level, opening condition, etc. |
| Heating thermostats | 4 | Operating modes, setpoint / actual temperature, valve position, etc. |
| Actuators | 1 | Level (roller shutter, dimmer), running direction (roller blind), etc. |
| Devices with measuring function | 3 | Status |
| | 6 | Consumption meter, voltage, power, etc. |

## FAQ

## Changelog
### 1.14.23 (2020-09-03)
* (foxriver76) `value.temperature` will have unit °C no matter of delivered unit by CCU

### 1.14.21 (2020-08-18)
* (foxriver76) fixed virtual-devices objects being recreated on instance startage (#271)

### 1.14.20 (2020-08-17)
* (foxriver76) fix for % scaling of float numbers

### 1.14.19 (2020-08-16)
* (foxriver76) now logging exact command on error

### 1.14.18 (2020-08-08)
* (foxriver76) fix issue when CuxD listDevices does not deliver valid array
* (foxriver76) fix error with % scaling in some edge cases

### 1.14.15 (2020-07-21)
* (foxriver76) fix bug on forced reinitialization run

### 1.14.14 (2020-07-10)
* (bluefox) Added roles for presence sensor

### 1.14.13 (2020-07-07)
* (foxriver76) fix edge case on EPAPER command (IOBROKER-HM-RPC-5Z)
* (foxriver76) Catch error on `createDevices` if CCU does not deliver valid ADDRESS (IOBROKER-HM-RPC-5X)

### 1.14.12 (2020-07-03)
* (foxriver76) Continue execution if error on retrieving a paramset from CCU

### 1.14.11 (2020-06-21)
* (bluefox) Change name of Instance according to the role (RF, Wired, HMIP)

### 1.14.10 (2020-06-14)
* (foxriver76) removed meta data caching completely because meta data can be dynamic due to FW update or CuxD

### 1.14.6 (2020-06-05)
* (foxriver76) added some hmip roles for channel 0

### 1.14.5 (2020-05-29)
* (foxriver76) fixed edge case problem IOBROKER-HM-RPC-5E

### 1.14.4 (2020-05-28)
* (jens-maus) updated all device images to latest ones include hmip-wired ones

### 1.14.3 (2020-05-18)
* (foxriver76) catch edge case error if row.value has no native 

### 1.14.2 (2020-04-24)
* (foxriver76) catch errors on rpc client creation

### 1.14.1 (2020-04-23)
* (foxriver76) catch potential errors on createServer
* (foxriver76) new meta data approach: we only store meta data gathered by the user,
otherwise cached meta data can be very old and outdated, we have to monitor performance
of this approach (more requests to CCU on first setup)
* (foxriver76) add name and icon to meta folder
* (foxriver76) minor code improvements

### 1.13.0 (2020-04-02)
* (foxriver76) sentry plugin support

### 1.12.10 (2020-03-05)
* (foxriver76) fixed no 'dpType for ..' error in all cases

### 1.12.9 (2020-02-29)
* (foxriver76) replace DISPLAY_DATA_STRING by DIN_66003 encodings

### 1.12.8 (2020-02-26)
* (foxriver76) improved error handling on undefined methods

### 1.12.7 (2020-02-16)
* (foxriver76) if role "value.window" is a boolean it is now correctly a "sensor.window"

### 1.12.6 (2020-01-08)
* (foxriver76) make all LEVEL dps of unit % if they are w.o. unit and have min/max

### 1.12.5 (2020-01-06)
* (foxriver76) handle some meta data more abstract
* (foxriver76) make DIMMER_REAL.LEVEL of unit '%' even it is not by definition

### 1.12.2 (2019-12-19)
* (foxriver76) fix issue on https with less robust ccu emulations

### 1.12.1 (2019-12-06)
* (foxriver76) fixed problem with max values of value lists

### 1.12.0 (2019-12-05)
* (foxriver76) no longer use adapter.objects
* (foxriver76) js-controller v > 2 required

### 1.11.1 (2019-11-20)
* (foxriver76) LOCK.OPEN is now of type button to prevent misunderstandings

### 1.11.0 (2019-11-10)
* (foxriver76) make OFFSET and REPEATS of epaper configurable
* (foxriver76) EPAPER_SIGNAL is now type string

### 1.10.3 (2019-10-27)
* (foxriver76) fixed info channel

### 1.10.2 (2019-10-24)
* (foxriver76) replace min max values of hmip with correct numbers 

### 1.10.0 (2019-08-12)
* (foxriver76) new meta data handling procedure
* __js-controller >= 1.4.2 required__

### Older entries
[here](OLD_CHANGELOG.md)

## License

The MIT License (MIT)

Copyright (c) 2014-2020 bluefox <dogafox@gmail.com>

Copyright (c) 2014 hobbyquaker

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.