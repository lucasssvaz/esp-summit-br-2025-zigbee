---
layout: two-cols
layoutClass: gap-16
---

# Device Discovery & Setup

**Getting devices into Home Assistant**

## Pairing Process
- **Enable pairing** - click Add Zigbee device
- **Device activation** - power on ESP32 device (auto-joins), must be in factory new state
- **Network scanning** - device finds coordinator automatically
- **Entity creation** - HA creates entities based on endpoints

## Troubleshooting
- **Factory reset** - long button press if device won't join
- **Low LQI** - move device closer to coordinator or add router devices

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Setup Checklist</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col space-y-2 text-xs">
        <div class="flex items-center space-x-2">
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
          <span>ZHA permit joining enabled</span>
        </div>
        <div class="flex items-center space-x-2">
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
          <span>ESP32 device powered on</span>
        </div>
        <div class="flex items-center space-x-2">
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
          <span>Device auto-joins network</span>
        </div>
        <div class="flex items-center space-x-2">
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
          <span>Entities appear in HA</span>
        </div>
      </div>
    </div>
  </div>
</div> 
