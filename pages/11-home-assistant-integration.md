---
layout: two-cols
layoutClass: gap-16
---

# Home Assistant Integration

**Seamless Zigbee device integration**

## Auto-Discovery
- **Zigbee2MQTT** - popular coordinator
- **ZHA** - Home Assistant's built-in
- **Zigbee2Tasmota** - Tasmota integration
- **Automatic pairing** - no manual config

## Device Recognition
- **Standard clusters** - recognized automatically
- **Device profiles** - proper entity creation
- **State reporting** - real-time updates
- **Command support** - full control

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Integration Flow</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col space-y-3">
        <div class="flex items-center space-x-2">
          <div class="w-6 h-6 bg-blue-500 rounded-full flex items-center justify-center text-white text-xs">1</div>
          <span class="text-sm">Device joins network</span>
        </div>
        <div class="w-1 h-4 bg-gray-400 ml-3"></div>
        <div class="flex items-center space-x-2">
          <div class="w-6 h-6 bg-green-500 rounded-full flex items-center justify-center text-white text-xs">2</div>
          <span class="text-sm">Coordinator detects device</span>
        </div>
        <div class="w-1 h-4 bg-gray-400 ml-3"></div>
        <div class="flex items-center space-x-2">
          <div class="w-6 h-6 bg-purple-500 rounded-full flex items-center justify-center text-white text-xs">3</div>
          <span class="text-sm">HA creates entities</span>
        </div>
        <div class="w-1 h-4 bg-gray-400 ml-3"></div>
        <div class="flex items-center space-x-2">
          <div class="w-6 h-6 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">4</div>
          <span class="text-sm">Ready for automation</span>
        </div>
      </div>
    </div>
  </div>
</div> 
