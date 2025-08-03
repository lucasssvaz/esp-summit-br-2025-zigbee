---
layout: two-cols
layoutClass: gap-16
class: text-base
---

# Zigbee Device Roles

**Three types of devices in a Zigbee network**

## Coordinator
- **Network manager** - Forms the network
- **Always powered** - Mains connected
- **Single per network** - Entry point
- **Stores network info** - Security keys

## Router
- **Data relay** - Extends network range
- **Always listening** - Mains powered
- **Multiple allowed** - Mesh backbone
- **Can join devices** - Parent role

::right::

## End Device
- **Battery powered** - Sleep mode
- **Limited range** - Direct connection
- **Simple operation** - Sensors/actuators
- **Parent dependent** - Router/coordinator

<div class="grid grid-cols-1 gap-4 mt-2">
  <div class="text-center">
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
