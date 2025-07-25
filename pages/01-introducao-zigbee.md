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

<div class="mt-14"></div>
<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h5 class="text-lg font-semibold mb-2">Zigbee Node Types</h5>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-3 gap-4 items-center">
        <div class="flex flex-col items-center">
          <div class="w-6 h-6 bg-red-500 rounded-full mb-2"></div>
          <div class="text-sm text-center">Coordinator</div>
        </div>
        <div class="flex flex-col items-center">
          <div class="w-6 h-6 bg-orange-500 rounded-full mb-2"></div>
          <div class="text-sm text-center">Router</div>
        </div>
        <div class="flex flex-col items-center">
          <div class="w-6 h-6 bg-green-500 rounded-full mb-2"></div>
          <div class="text-sm text-center">End Device</div>
        </div>
      </div>
    </div>
  </div>
</div> 

::right::

<div class="flex items-center justify-center h-full">
  <div class="scale-75">
    <ZigbeeGraph />
  </div>
</div>
