---
layout: two-cols
layoutClass: gap-16
---

# Zigbee Endpoints

**Building blocks for device functionality**

## Endpoints Classes
- **Virtual interfaces** - up to 240 per device
- **Independent functions** - each serves specific purpose
- **Cluster groups** - related functionality bundled
- **Device identification** - profile and device IDs

## Supported Endpoins
- **Basic** - binary, analog and multistate input/output
- **Switches** - on/off, color dimmable, power outlet, contact switch
- **Lights** - on/off, dimmable, color dimmable
- **Controllers** - thermostat, fan control
- **Sensors** - temperature, humidity, CO2, illuminance and more
- **Occupancy** - motion sensor
- **Others** - gateway, range extender

::right::

//TODO: add screenshot or list of EP classes:

// Endpoints
//// Switches
#include "ep/ZigbeeColorDimmerSwitch.h"
#include "ep/ZigbeeSwitch.h"
//// Lights
#include "ep/ZigbeeColorDimmableLight.h"
#include "ep/ZigbeeDimmableLight.h"
#include "ep/ZigbeeLight.h"
//// Controllers
#include "ep/ZigbeeThermostat.h"
#include "ep/ZigbeeFanControl.h"
////Outlets
#include "ep/ZigbeePowerOutlet.h"
//// Sensors
#include "ep/ZigbeeAnalog.h"
#include "ep/ZigbeeBinary.h"
#include "ep/ZigbeeCarbonDioxideSensor.h"
#include "ep/ZigbeeContactSwitch.h"
#include "ep/ZigbeeDoorWindowHandle.h"
#include "ep/ZigbeeElectricalMeasurement.h"
#include "ep/ZigbeeFlowSensor.h"
#include "ep/ZigbeeIlluminanceSensor.h"
#include "ep/ZigbeeMultistate.h"
#include "ep/ZigbeeOccupancySensor.h"
#include "ep/ZigbeePM25Sensor.h"
#include "ep/ZigbeePressureSensor.h"
#include "ep/ZigbeeTempSensor.h"
#include "ep/ZigbeeVibrationSensor.h"
#include "ep/ZigbeeWindSpeedSensor.h"
#include "ep/ZigbeeWindowCovering.h"
//// Other
#include "ep/ZigbeeGateway.h"
#include "ep/ZigbeeRangeExtender.h"

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">List of EP Classes Clusters</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-2 gap-2 text-xs">
        <div class="bg-blue-100 p-2 rounded">
          <div class="font-bold">Basic</div>
          <div>Device info</div>
        </div>
        <div class="bg-green-100 p-2 rounded">
          <div class="font-bold">On/Off</div>
          <div>Switch control</div>
        </div>
        <div class="bg-purple-100 p-2 rounded">
          <div class="font-bold">Level</div>
          <div>Dimmer control</div>
        </div>
        <div class="bg-orange-100 p-2 rounded">
          <div class="font-bold">Temperature</div>
          <div>Temp sensor</div>
        </div>
        <div class="bg-red-100 p-2 rounded">
          <div class="font-bold">Humidity</div>
          <div>Humidity sensor</div>
        </div>
        <div class="bg-yellow-100 p-2 rounded">
          <div class="font-bold">Occupancy</div>
          <div>Motion sensor</div>
        </div>
      </div>
    </div>
  </div>
</div> 
