---
layout: two-cols
layoutClass: gap-16
---

# Zigbee Endpoints

**Building blocks for device functionality**

## Endpoints Classes
- **Virtual interfaces** - Up to 240 per device
- **Independent functions** - Each serves specific purpose
- **Cluster groups** - Related functionality bundled
- **Device identification** - Profile and device IDs

::right::

<div class="grid grid-cols-1 gap-4 mt-12">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Examples of Endpoints</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-2 gap-2 text-xs">
        <div class="bg-blue-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Basic</div>
          <div>Binary, analog, multistate I/O</div>
        </div>
        <div class="bg-green-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Switches</div>
          <div>On/off, color dimmable, power outlet, contact switch</div>
        </div>
        <div class="bg-purple-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Lights</div>
          <div>On/off, dimmable, color dimmable</div>
        </div>
        <div class="bg-orange-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Controllers</div>
          <div>Thermostat, fan control</div>
        </div>
        <div class="bg-red-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Sensors</div>
          <div>Temperature, humidity, CO2, illuminance</div>
        </div>
        <div class="bg-yellow-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Others</div>
          <div>Gateway, range extender</div>
        </div>
      </div>
    </div>
  </div>
</div> 

- For more information and other endpoints, see the [documentation](https://docs.espressif.com/projects/arduino-esp32/en/latest/zigbee/zigbee.html).
