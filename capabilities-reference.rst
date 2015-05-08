.. _capabilities_taxonomy:

Capabilities Reference
======================

Capabilities are core to the SmartThings architecture.
They allow us to abstract specific devices into their underlying capabilities.


An application interacts with devices based on their capabilities, so once we understand the capabilities that are needed by a SmartApp, and the capabilities that are provided by a device, we can understand which devices (based on the Device's declared capabilities) are eligible for use within a specific SmartApp.

Capabilities themselves are decomposed into both Commands and Attributes.
Commands represent ways in which you can control or actuate the device, whereas Attributes represent state information or properties of the device.

Capabilities are created and maintained by the SmartThings internal development team.


This page serves as a reference for the supported capabilities.

.. note::

    This document is a work in progress.
    Many capabilities are not yet fully documented.
    We are continually working to document all the capabilities.

At a Glance
-----------

The Capabilities reference table below lists all capabilities. The various columns are:

Name:
    The name of the capability that is used by a Device Handler.
Preferences Reference:
    The string you would use in a SmartApp to allow a user to select from devices supporting this capability.
Attributes:
    The attributes that the capability defines.
Commands:
    The commands (and their signatures) that the capability defines.

============================= ====================================== ===================================== ========================
       Name                   Preferences Reference                  Attributes                            Commands
============================= ====================================== ===================================== ========================
:ref:`acceleration-sensor`    capability.accelerationSensor          - acceleration

:ref:`actuator`               capability.actuator
:ref:`alarm`                  capability.alarm                       - alarm                               - off()
                                                                                                           - strobe()
                                                                                                           - siren()
                                                                                                           - both()

:ref:`battery`                capability.battery                     - battery
:ref:`beacon`                 capability.beacon                      - presence
:ref:`button`                 capability.button                      - button
:ref:`c_m_detector`           capability.carbonMonoxideDetector      - carbonMonoxide
:ref:`color_control`          capability.colorControl                - hue                                 - setHue(number)

                                                                     - saturation                          - setSaturation(number)
                                                                     - color                               - setColor(color_map)
:ref:`configuration`          capability.configuration                                                     - configure()
:ref:`contact_sensor`         capability.contactSensor               - contact
:ref:`door_control`           capability.doorControl                 - door                                - open()
                                                                                                           - close()
:ref:`energy_meter`           capability.energyMeter                 - energy
:ref:`illuminance_mesurmnt`   capability.illuminanceMeasurement      - illuminance
:ref:`image_capture`          capability.imageCapture                - image                               - take()
:ref:`indicator`              capability.indicator                   - indicatorStatus                     - indicatorWhenOn()
                                                                                                           - indicatorWhenOff()
                                                                                                           - indicatorNever()
:ref:`location_mode`          capability.locationMode                - mode
:ref:`lock`                   capability.lock                        - lock                                - lock()
                                                                                                           - unlock()
:ref:`lock_codes`             capability.lockCodes                   - lock                                - lock()
                                                                     - codeReport                          - unlock()
                                                                     - codeChanged                         - updateCodes(json_object)
                                                                                                           - setCode(number\, string)
                                                                                                           - deleteCode(number)
                                                                                                           - requestCode(number)
                                                                                                           - reloadAllCodes()
:ref:`media_controller`       capability.mediaController             - activities                          - startActivity(string)
                                                                     - currentActivity                     - getAllActivities()
                                                                                                           - getCurrentActivity()
:ref:`momentary`              capability.momentary                                                         - push()
:ref:`motion_sensor`          capability.motionSensor                - motion
:ref:`music_player`           capability.musicPlayer                 - status                              - play()
                                                                     - level                               - pause()
                                                                     - trackDescription                    - stop()
                                                                     - trackData                           - nextTrack()
                                                                     - mute                                - playTrack(string)
                                                                                                           - setLevel(number)
                                                                                                           - playText(string)
                                                                                                           - mute()
                                                                                                           - previousTrack()
                                                                                                           - unmute()
                                                                                                           - setTrack(string)
                                                                                                           - resumeTrack(string)
                                                                                                           - restoreTrack(string)
:ref:`polling`                capability.polling                                                           - poll()
:ref:`power_meter`            capability.powerMeter                  - power
:ref:`presence_sensor`        capability.presenceSensor              - presence
:ref:`refresh`                capability.refresh                                                           - refresh()
:ref:`rel_hmdty_mesurmnt`     capability.relativeHumidityMeasurement - humidity
:ref:`relay_switch`           capability.relaySwitch                 - switch                              - on()
                                                                                                           - off()
:ref:`sensor`                 capability.sensor
:ref:`signal_strength`        capability.signalStrength              - lqi
                                                                     - rssi

:ref:`sleep_sensor`           capability.sleepSensor                 - sleeping
:ref:`smoke_detector`         capability.smokeDetector               - smoke
:ref:`speech_synthesis`       capability.speechSynthesis                                                   - speak(string)
:ref:`step_sensor`            capability.stepSensor                  - steps
                                                                     - goal
:ref:`switch`                 capability.switch                      - switch                              - on()
                                                                                                           - off()
:ref:`switch_level`           capability.switchLevel                 - level                               - setLevel(number, number)
:ref:`temp_measurement`       capability.temperatureMeasurement      - temperature
:ref:`thermostat`             capability.thermostat                  - temperature                         - setHeatingSetpoint(number)
                                                                     - heatingSetpoint                     - setCoolingSetpoint(number)
                                                                     - coolingSetpoint                     - off()
                                                                     - thermostatSetpoint                  - heat()
                                                                     - thermostatMode                      - emergencyHeat()
                                                                     - thermostatFanMode                   - cool()
                                                                     - thermostatOperatingState            - setThermostatMode(enum)
                                                                                                           - fanOn()
                                                                                                           - fanAuto()
                                                                                                           - fanCirculate()
                                                                                                           - setThermostatFanMode(enum)
                                                                                                           - auto()
:ref:`therm_cooling_setpoint` capability.thermostatCoolingSetpoint   - coolingSetpoint                     - setCoolingSetpoint(number)
:ref:`thermostat_fan_mode`    capability.thermostatFanMode           - thermostatFanMode                   - fanOn()
                                                                                                           - fanAuto()
                                                                                                           - fanCirculate()
                                                                                                           - setThermostatFanMode(enum)
:ref:`therm_heating_setpoint` capability.thermostatHeatingSetpoint   - heatingSetpoint                     - setHeatingSetpoint(number)
:ref:`thermostat_mode`        capability.thermostatMode              - thermostatMode                      - off()
                                                                                                           - heat()
                                                                                                           - emergencyHeat()
                                                                                                           - cool()
                                                                                                           - auto()
                                                                                                           - setThermostatMode(enum)
:ref:`therm_operating_state`  capability.thermostatOperatingState    - thermostatOperatingState
:ref:`thermostat_setpoint`    capability.thermostatSetpoint          - thermostatSetpoint
:ref:`three_axis`             capability.threeAxis                   - threeAxis
:ref:`tone`                   capability.tone                                                              - beep()
:ref:`touch_sensor`           capability.touchSensor                 - touch
:ref:`valve`                  capability.valve                       - contact                             - open()
                                                                                                           - close()
:ref:`water_sensor`           capability.waterSensor                 - water
============================= ====================================== ===================================== ========================

.. _acceleration-sensor:

Acceleration Sensor
-------------------

The Acceleration Sensor capability allows for acceleration detection.

Some use cases for SmartApps using this capability would be detecting if a washing machine is vibrating, or if a case has moved (particularly useful for knowing if a weapon case has been moved).

==================== =====================
Capability Name      Preferences Reference
==================== =====================
Acceleration Sensor  capability.accelerationSensor
==================== =====================

**Attributes:**

============ ====== ===============
Attribute    Type   Possible Values
============ ====== ===============
acceleration String ``"active"`` if acceleration is detected.

                    ``"inactive"`` if no acceleration is detected.
============ ====== ===============

**Commands:**

None.

**SmartApp Example**

.. code-block:: groovy

    // preferences reference
    preferences {
        input "accelerationSensor", "capability.accelerationSensor"
    }

    def installed() {
        // subscribe to active acceleration
        subscribe(accelerationSensor, "acceleration.active",
                  accelerationActiveHandler)

        // subscribe to inactive acceleration
        subscribe(accelerationSensor, "acceleration.inactive",
                  accelerationInactiveHandler)

        // subscribe to all acceleration events
        subscribe(accelerationSensor, "acceleration", accelerationBothHandler)
    }



.. _actuator:

Actuator
--------

The Actuator capability is a "tagging" capability. It defines no attributes or commands.

In SmartThings terms, it represents that a Device has commands.

----

.. _alarm:

Alarm
-----

The Alarm capability allows for interacting with devices that serve as alarms.

.. note::

    Z-Wave sometimes uses the term "Alarm" to refer to an important notification.
    The *Alarm* Capability is used in SmartThings to define a device that acts as an Alarm in the traditional sense (e.g., has a siren and such).

+------------------+--------------------------------+
| Capability Name  | SmartApp Preferences Reference |
+==================+================================+
| Alarm            | capability.alarm               |
+------------------+--------------------------------+

**Attributes:**

=========   =========   ===============
Attribute   Type        Possible Values
=========   =========   ===============
alarm       String      ``"strobe"`` if the alarm is strobing.

                        ``"siren"`` if the alarm is sounding the siren.

                        ``"off"`` if the alarm is turned off.

                        ``"both"`` if the alarm is strobing and sounding the alarm.
=========   =========   ===============

**Commands:**

*strobe()*
    Strobe the alarm

*siren()*
    Sound the siren on the alarm

*both()*
    Strobe and sound the alarm

*off()*
    Turn the alarm (siren and strobe) off

**SmartApp Example:**

.. code-block:: groovy

    // preferences reference
    preferences {
        input "alarm", "capability.alarm"
    }

    def installed() {
        // subscribe to alarm strobe
        subscribe(alarm, "alarm.strobe", strobeHandler)

        // subscribe to all alarm events
        subscribe(alarm, "alarm", allAlarmHandler)
    }

    def strobeHandler(evt) {
        log.debug "${evt.value}" // => "strobe"
    }

    def allAlarmHandler(evt) {
        if (evt.value == "strobe") {
            log.debug "alarm strobe"
        } else if (evt.value == "siren") {
            log.debug "alarm siren"
        } else if (evt.value == "both") {
            log.debug "alarm siren and alarm"
        } else if (evt.value == "off") {
            log.debug "alarm turned off"
        } else {
            log.debug "unexpected event: ${evt.value}"
        }
    }

----

.. _battery:

Battery
-------

Defines that the device has a battery.

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Battery          capability.battery
================ ==============================

**Attributes:**

========== ======= ===============
Attribute  Type    Possible Values
========== ======= ===============
battery
========== ======= ===============

**Commands:**

None

**SmartApp Example:**

.. code-block:: groovy

    preferences {
        section() {
            input "thebattery", "capability.battery"
        }
    }

    def installed() {
        def batteryValue = thebattery.latestValue("battery")
        log.debug "latest battery value: $batteryValue"

        subscribe(thebattery, "battery", batteryHandler)
    }

    def batteryHandler(evt) {
        log.debug "battery attribute changed to ${evt.value}"
    }

----

.. _beacon:

Beacon
------

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Beacon           capability.beacon
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
presence    String  ``"present"``
                    ``"not present"``
=========== ======= =================

**Commands:**

None.

**SmartApp Example:**

.. code-block:: groovy

    preferences {
        section() {
            input "thebeacon", "capability.beacon"
        }
    }

    def installed() {
        def currBeacon = thebeacon.currentValue("presence")
        log.debug "beacon is currently: $currBeacon"

        subscribe(thebeacon, "presence", beaconHandler)
    }

    def beaconHandler(evt) {
        log.debug "beacon presence is: ${evt.value}"
    }

----

.. _button:

Button
------

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Button           capability.button
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
button      String  ``"held"``
                    ``"pushed"``
=========== ======= =================

**Commands:**

None.

----

.. _c_m_detector:

Carbon Monoxide Detector
------------------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Carbon Monoxide Detector    capability.carbonMonoxideDetector
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
carbonMonoxide  String  ``"tested"``
                        ``"clear"``
                        ``"detected"``
=============== ======= =================

**Commands:**

None.

----

.. _color_control:

Color Control
-------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Color Control               capability.colorControl
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
hue             Number  0-255
saturation      Number  0-255
color           Map
=============== ======= =================

**Commands:**

*setHue(number)*
    Sets the colors hue value
*setSaturation(number)*
    Sets the colors saturation value
*setColor(color_map)*
    Sets the color to the passed in maps values

----

.. _configuration:

Configuration
-------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Configuration               capability.configuration
=========================   ==============================

**Attributes:**

None.

**Commands:**

*configure()*
    Configure

----

.. _contact_sensor:

Contact Sensor
--------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Contact Sensor              capability.contactSensor
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
contact         String  ``"open"``
                        ``"closed"``
=============== ======= =================

**Commands:**

None.

----

.. _door_control:

Door Control
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Door Control                capability.doorControl
=========================   ==============================

**Attributes:**

========= ======= =================
Attribute Type    Possible Values
========= ======= =================
door      String  ``"unknown"``
                  ``"closed"``
                  ``"open"``
                  ``"closing"``
                  ``"opening"``
========= ======= =================

**Commands:**

*open()*
    Opens the door
*close()*
    Closes the door

----

.. _energy_meter:

Energy Meter
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Energy Meter                capability.energyMeter
=========================   ==============================

**Attributes:**

========= ======= =================
Attribute Type    Possible Values
========= ======= =================
door
========= ======= =================

**Commands:**

None.

----

.. _illuminance_mesurmnt:

Illuminance Measurement
-----------------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Illuminance Measurement     capability.illuminanceMeasurement
=========================   ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
illuminance
=========== ======= =================

**Commands:**

None.

----

.. _image_capture:

Image Capture
-------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Image Capture               capability.imageCapture
=========================   ==============================

**Attributes:**

========= ======= =================
Attribute Type    Possible Values
========= ======= =================
image
========= ======= =================

**Commands:**

*take()*
    Capture an image

----

.. _indicator:

Indicator
---------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Indicator                   capability.indicator
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
indicatorStatus String  ``"when on"``
                        ``"never"``
                        ``"when off"``
=============== ======= =================

**Commands:**

*indicatorWhenOn()*

*indicatorWhenOff()*

*indicatorNever()*

----

.. _location_mode:

Location Mode
-------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Location Mode               capability.locationMode
=========================   ==============================

**Attributes:**

========= ======= =================
Attribute Type    Possible Values
========= ======= =================
mode
========= ======= =================

**Commands:**

None.

----

.. _lock:

Lock
----

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Lock                        capability.lock
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
lock            String  ``"locked"``
                        ``"unlocked"``
=============== ======= =================

**Commands:**

*lock()*
    Lock the device
*unlock()*
    Unlock the device

----

.. _lock_codes:

Lock Codes
----------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Lock Codes                  capability.lockCodes
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
lock
codeReport
codeChanged
=============== ======= =================

**Commands:**

*lock()*
    Lock the device
*unlock()*
    Unlock the device
*updateCodes(json_object)*
    Update the lock code with the given json object
*setCode(number, string)*
    Set the lock code
*deleteCode(number)*
    Delete a lock code
*requestCode(number)*
    Request a lock code
*reloadAllCodes()*
    Reload all lock codes

----

.. _media_controller:

Media Controller
----------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Media Controller            capability.mediaController
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
activities
currentActivity
=============== ======= =================

**Commands:**

*startActivity(string)*
    Start the activity with the given name
*getAllActivities()*
    Get a list of all the activities
*getCurrentActivity()*
    Get the current activity

----

.. _momentary:

Momentary
---------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Momentary                   capability.momentary
=========================   ==============================

**Attributes:**

None.

**Commands:**

*push()*
    Press the momentary switch

----

.. _motion_sensor:

Motion Sensor
-------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Motion Sensor               capability.motionSensor
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
motion          String  ``"active"``
                        ``"inactive"``
=============== ======= =================

**Commands:**

None.

----

.. _music_player:

Music Player
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Music Player                capability.musicPlayer
=========================   ==============================

**Attributes:**

================ ======= =================
Attribute        Type    Possible Values
================ ======= =================
status
level
trackDescription
trackData
mute             String  ``"muted"``
                         ``"unmuted"``
================ ======= =================

**Commands:**

*play()*
    Start music playback
*pause()*
    Pause music playback
*stop()*
    Stop music playback
*nextTrack()*
    Advance to next track
*playTrack(string)*
    Play the track matching the given string
*setLevel(number)*
    Set the volume to the specified level
*playText(string)*
    Set the text of the currently playing track
*mute()*
    Mute playback
*previousTrack()*
    Go back to the previous track
*unmute()*
    Unmute playback
*setTrack(string)*
    Set the track text to the string passed in
*resumeTrack(string)*
    Resume music playback
*restoreTrack(string)*
    Restore the track with the given name

----

.. _polling:

Polling
-------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Polling                     capability.polling
=========================   ==============================

**Attributes:**

None.

**Commands:**

*poll()*
    Poll devices

----

.. _power_meter:

Power Meter
-----------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Power Meter                 capability.powerMeter
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
power
=============== ======= =================

**Commands:**

None.

----

.. _presence_sensor:

Presence Sensor
---------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Presence Sensor             capability.presenceSensor
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
Presence        String  ``"present"``
                        ``"not present"``
=============== ======= =================

**Commands:**

None.

----

.. _refresh:

Refresh
-------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Refresh                     capability.refresh
=========================   ==============================

**Attributes:**

None.

**Commands:**

*refresh()*
    Refresh

----

.. _rel_hmdty_mesurmnt:

Relative Humidity Measurement
-----------------------------

=============================   ==============================
Capability Name                 SmartApp Preferences Reference
=============================   ==============================
Relative Humidity Measurement   capability.relativeHumidityMeasurement
=============================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
humidity
=============== ======= =================

**Commands:**

None.

----

.. _relay_switch:

Relay Switch
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Relay Switch                capability.relaySwitch
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
switch          String  ``"off"``
                        ``"on"``
=============== ======= =================

**Commands:**

*off()*
    Turn the switch off
*on()*
    Turn the switch on

----

.. _sensor:

Sensor
------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Sensor                      capability.sensor
=========================   ==============================

**Attributes:**

None.

**Commands:**

None.

----

.. _signal_strength:

Signal Strength
---------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Signal Strength             capability.signalStrength
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
lqi
rssi
=============== ======= =================

**Commands:**

None.

----

.. _sleep_sensor:

Sleep Sensor
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Sleep Sensor                capability.sleepSensor
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
sleeping        String  ``"not sleeping"``
                        ``"sleeping"``
=============== ======= =================

**Commands:**

None.

----

.. _smoke_detector:

Smoke Detector
--------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Smoke Detector              capability.smokeDetector
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
smoke           String  ``"detected"``
                        ``"clear"``
                        ``"tested"``
=============== ======= =================

**Commands:**

None.

----

.. _speech_synthesis:

Speech Synthesis
----------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Speech Synthesis            capability.speechSynthesis
=========================   ==============================

**Attributes:**

None.

**Commands:**

*speak(string)*
    It can talk!
----

.. _step_sensor:

Step Sensor
-----------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Step Sensor                 capability.stepSensor
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
steps
goal
=============== ======= =================

**Commands:**

None.

----

.. _switch:

Switch
------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Switch                      capability.switch
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
switch          String  ``"off"``
                        ``"on"``
=============== ======= =================

**Commands:**

*on()*
    Turn the switch on
*off()*
    Turn the switch off

----

.. _switch_level:

Switch Level
------------

=========================   ==============================
Capability Name             SmartApp Preferences Reference
=========================   ==============================
Switch Level                capability.switchLevel
=========================   ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
level
=============== ======= =================

**Commands:**

*setLevel(number, number)*
    Set the level to the given numbers

----

.. _temp_measurement:

Temperature Measurement
-----------------------

=========================== ==============================
Capability Name             SmartApp Preferences Reference
=========================== ==============================
Temperature Measurement     capability.temperatureMeasurement
=========================== ==============================

**Attributes:**

======================== ======= =================
Attribute                Type    Possible Values
======================== ======= =================
temperature
======================== ======= =================

**Commands:**

None.

----

.. _thermostat:

Thermostat
----------

=========================== ==============================
Capability Name             SmartApp Preferences Reference
=========================== ==============================
Thermostat                  capability.thermostat
=========================== ==============================

**Attributes:**

======================== ======= =================
Attribute                Type    Possible Values
======================== ======= =================
temperature
heatingSetpoint
coolingSetpoint
thermostatSetpoint
thermostatMode           String  ``"auto"``
                                 ``"emergency heat"``
                                 ``"heat"``
                                 ``"off"``
                                 ``"cool"``
thermostatFanMode        String  ``"auto"``
                                 ``"on"``
                                 ``"circulate"``
thermostatOperatingState String  ``"heating"``
                                 ``"idle"``
                                 ``"pending cool"``
                                 ``"vent economizer"``
                                 ``"cooling"``
                                 ``"pending heat"``
                                 ``"fan only"``
======================== ======= =================

**Commands:**

*setHeatingSetpoint(number)*

*setCoolingSetpoint(number)*

*off()*

*heat()*

*emergencyHeat()*

*cool()*

*setThermostatMode(enum)*

*fanOn()*

*fanAuto()*

*fanCirculate()*

*setThermostatFanMode(enum)*

*auto()*

----

.. _therm_cooling_setpoint:

Thermostat Cooling Setpoint
---------------------------

=========================== ==============================
Capability Name             SmartApp Preferences Reference
=========================== ==============================
Thermostat Cooling Setpoint capability.thermostatCoolingSetpoint
=========================== ==============================

**Attributes:**

================== ======= =================
Attribute          Type    Possible Values
================== ======= =================
coolingSetpoint
================== ======= =================

**Commands:**

*setCoolingSetpoint(number)*

----

.. _thermostat_fan_mode:

Thermostat Fan Mode
-------------------

=========================== ==============================
Capability Name             SmartApp Preferences Reference
=========================== ==============================
Thermostat Fan Mode         capability.thermostatFanMode
=========================== ==============================

**Attributes:**

================== ======= =================
Attribute          Type    Possible Values
================== ======= =================
thermostatFanMode  String  ``"on"``
                           ``"auto"``
                           ``"circulate"``
================== ======= =================

**Commands:**

*fanOn()*

*fanAuto()*

*fanCirculate()*

*setThermostatFanMode(enum)*

----

.. _therm_heating_setpoint:

Thermostat Heating Setpoint
---------------------------

=========================== ==============================
Capability Name             SmartApp Preferences Reference
=========================== ==============================
Thermostat Heating Setpoint capability.thermostatHeatingSetpoint
=========================== ==============================

**Attributes:**

=============== ======= =================
Attribute       Type    Possible Values
=============== ======= =================
heatingSetpoint
=============== ======= =================

**Commands:**

*setHeatingSetpoint(number)*

----

.. _thermostat_mode:

Thermostat Mode
---------------

========================== ==============================
Capability Name            SmartApp Preferences Reference
========================== ==============================
Thermostat Mode            capability.thermostatMode
========================== ==============================

**Attributes:**

============== ======= =================
Attribute      Type    Possible Values
============== ======= =================
thermostatMode String  ``"emergency heat"``
                       ``"heat"``
                       ``"cool"``
                       ``"off"``
                       ``"auto"``
============== ======= =================

**Commands:**

*off()*

*heat()*

*emergencyHeat()*

*cool()*

*auto()*

*setThermostatMode(enum)*

----

.. _therm_operating_state:

Thermostat Operating State
--------------------------

========================== ==============================
Capability Name            SmartApp Preferences Reference
========================== ==============================
Thermostat Operating State capability.thermostatOperatingState
========================== ==============================

**Attributes:**

======================== ======= ======================
Attribute                Type    Possible Values
======================== ======= ======================
thermostatOperatingState String  ``"idle"``
                                 ``"fan only"``
                                 ``"vent economizer"``
                                 ``"cooling"``
                                 ``"pending heat"``
                                 ``"heating"``
                                 ``"pending cool"``
======================== ======= ======================

**Commands:**

None.

----

.. _thermostat_setpoint:

Thermostat Setpoint
-------------------

=================== ==============================
Capability Name     SmartApp Preferences Reference
=================== ==============================
Thermostat Setpoint capability.thermostatSetpoint
=================== ==============================

**Attributes:**

=================== ======= =================
Attribute           Type    Possible Values
=================== ======= =================
thermostatSetpoint
=================== ======= =================

**Commands:**

None.

----


.. _three_axis:

Three Axis
----------

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Three Axis       capability.threeAxis
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
threeAxis
=========== ======= =================

**Commands:**

None.

----

.. _tone:

Tone
----

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Tone             capability.tone
================ ==============================

**Attributes:**

None.

**Commands:**

*beep()*
    Beep the device.

----

.. _touch_sensor:

Touch Sensor
------------

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Touch Sensor     capability.touchSensor
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
touch       String  ``"touched"``
=========== ======= =================

**Commands:**

None.

----

.. _valve:

Valve
-----

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Valve            capability.valve
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
contact     String  ``"closed"``
                    ``"open"``
=========== ======= =================

**Commands:**

=========== ========== =================
Command     Parameters Description
=========== ========== =================
open()
close()
=========== ========== =================

----

.. _water_sensor:

Water Sensor
------------

================ ==============================
Capability Name  SmartApp Preferences Reference
================ ==============================
Water Sensor     capability.waterSensor
================ ==============================

**Attributes:**

=========== ======= =================
Attribute   Type    Possible Values
=========== ======= =================
water       String  ``"dry"``
                    ``"wet"``
=========== ======= =================

**Commands:**

None.