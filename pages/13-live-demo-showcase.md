---
layout: two-cols
layoutClass: gap-16
---

# Live Demo Showcase

**Real-world Zigbee implementations**

## Demo Devices
- **Window Covering** - ESP32C6 + M5Stack Glass unit for simulating the window
- **Vibration detector** - ESP32-C6 + SW-420
- **CO2, tmperature and humidity sensor** - ESP32-C6 + SCD41

## Demo Scenarios
- **Live network status** - all devices connected via Zigbee dongle
- **Home Assistant dashboard** - real-time sensor data display
- **Automation triggers** - vibration detection control other demos LEDS
- **Window covers control** - Covers can be controlled from dashboard or buttons on display
- **Environmental monitoring** - temperature, humidity, CO2 tracking

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Demo Setup</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col space-y-3">
        <div class="flex items-center justify-between p-2 bg-blue-100 rounded">
          <span class="text-sm">HA running ZHA</span>
          <div class="w-3 h-3 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-green-100 rounded">
          <span class="text-sm">Window Covering</span>
          <div class="w-3 h-3 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-purple-100 rounded">
          <span class="text-sm">Vibration Detector</span>
          <div class="w-3 h-3 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-orange-100 rounded">
          <span class="text-sm">CO2/Temp/Humidity</span>
          <div class="w-3 h-3 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-red-100 rounded">
          <span class="text-sm">HA Automations</span>
          <div class="w-3 h-3 bg-green-500 rounded-full"></div>
        </div>
      </div>
      <div class="mt-3 text-xs text-gray-600">
        Live demo with working automations
      </div>
    </div>
  </div>
</div> 
