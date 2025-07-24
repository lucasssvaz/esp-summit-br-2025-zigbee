---
layout: two-cols
layoutClass: gap-16
---

# Espressif Zigbee Limitations

**Important considerations for development**

## Hardware Limitations
- **Single radio** - WiFi/Zigbee can't run simultaneously
- **Memory constraints** - limited RAM for large networks
- **Power consumption** - higher than dedicated Zigbee chips
- **Antenna design** - requires proper RF layout

## Development Considerations
- **Radio switching** - need to manage WiFi/Zigbee transitions
- **Memory management** - careful with dynamic allocation
- **Power optimization** - use sleep modes effectively
- **Network size** - practical limit ~50 devices per coordinator

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Radio Usage</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col space-y-3">
        <div class="flex items-center justify-between p-2 bg-blue-100 rounded">
          <span class="text-sm">WiFi Mode</span>
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-gray-100 rounded">
          <span class="text-sm">Zigbee Mode</span>
          <div class="w-4 h-4 bg-green-500 rounded-full"></div>
        </div>
        <div class="flex items-center justify-between p-2 bg-red-100 rounded">
          <span class="text-sm">Both Active</span>
          <div class="w-4 h-4 bg-red-500 rounded-full"></div>
        </div>
      </div>
      <div class="mt-3 text-xs text-gray-600">
        Radio switching required
      </div>
    </div>
  </div>
</div> 
