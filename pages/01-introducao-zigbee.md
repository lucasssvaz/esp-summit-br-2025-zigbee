---
layout: two-cols
layoutClass: gap-16
---

# Zigbee Protocol

**Low-power wireless mesh network protocol**

- **2.4 GHz** frequency band
- **IEEE 802.15.4** standard
- **Mesh networking** - devices relay data
- **Low latency** - < 100ms response
- **Interoperable** - Zigbee Alliance certified

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Zigbee Network Topology</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex justify-center items-center space-x-4 mb-4">
        <div class="w-8 h-8 bg-blue-500 rounded-full flex items-center justify-center text-white text-xs">C</div>
        <div class="text-sm">Coordinator</div>
      </div>
      <div class="flex justify-center items-center space-x-4 mb-2">
        <div class="w-6 h-6 bg-green-500 rounded-full flex items-center justify-center text-white text-xs">R</div>
        <div class="text-sm">Router</div>
      </div>
      <div class="flex justify-center items-center space-x-4">
        <div class="w-4 h-4 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
        <div class="text-sm">End Device</div>
      </div>
    </div>
  </div>
</div> 

::right::

<div class="scale-75 origin-top mx-auto">
  <ZigbeeGraph />
</div>
