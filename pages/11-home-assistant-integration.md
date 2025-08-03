---
layout: two-cols
layoutClass: gap-16
class: text-base
---

# Home Assistant Integration

**Seamless Zigbee device integration**

<div class="mt-4"></div>

## Auto-Discovery
- **ZHA** - Home Assistant's built-in Zigbee integration
- **Zigbee2MQTT** - Alternative integration with MQTT broker
- **Standard HA profile** - Arduino library uses Home Automation profile
- **Custom setup** - Needed for OTA updates or customised clusters

::right::

<div class="mt-10"></div>

## Device Recognition
- **Standard clusters** - Recognized automatically (On/Off, Level, etc.)
- **Device profiles** - Proper entity creation based on endpoint types
- **Automatic reporting** - Configured intervals send updates
- **Command support** - Bidirectional control (HA - device)
- **Battery monitoring** - Voltage and percentage for sleepy devices
