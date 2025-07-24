---
layout: two-cols
layoutClass: gap-16
---

# Zigbee Device Roles

**Three types of devices in a Zigbee network**

## Coordinator
- **Network manager** - forms the network
- **Always powered** - mains connected
- **Single per network** - entry point
- **Stores network info** - security keys

## Router
- **Data relay** - extends network range
- **Always listening** - mains powered
- **Multiple allowed** - mesh backbone
- **Can join devices** - parent role

## End Device
- **Battery powered** - sleep mode
- **Limited range** - direct connection
- **Simple operation** - sensors/actuators
- **Parent dependent** - router/coordinator

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Device Hierarchy</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col items-center space-y-3">
        <div class="w-12 h-12 bg-blue-600 rounded-full flex items-center justify-center text-white font-bold">C</div>
        <div class="text-xs text-gray-600">Coordinator</div>
        <div class="w-1 h-4 bg-gray-400"></div>
        <div class="flex space-x-4">
          <div class="w-10 h-10 bg-green-600 rounded-full flex items-center justify-center text-white font-bold">R</div>
          <div class="w-10 h-10 bg-green-600 rounded-full flex items-center justify-center text-white font-bold">R</div>
        </div>
        <div class="text-xs text-gray-600">Routers</div>
        <div class="w-1 h-4 bg-gray-400"></div>
        <div class="flex space-x-2">
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
        </div>
        <div class="text-xs text-gray-600">End Devices</div>
      </div>
    </div>
  </div>
</div> 
