---
layout: default
layoutClass: gap-16
class: text-base
---

# Espressif Zigbee Limitations

**Important considerations for development**

- **Radio switching** - Required to manage WiFi/Zigbee transitions. WiFi and Zigbee can't run simultaneously.
- **Memory management** - Limited RAM for large networks.
- **Power optimization** - Higher power consumption than Zigbee dedicated chips. Requires effective use of sleep modes.
- **Network size** - Practical limit of ~50 devices per coordinator.

<figure class="flex flex-col justify-center items-center">
  <img src="/images/esp-thread-border-router-board.png" alt="ESP Thread Border Router / Zigbee Gateway V1.2 Board" class="w-1/4" />
  <figcaption class="text-sm text-gray-600">ESP Thread Border Router / Zigbee Gateway V1.2</figcaption>
</figure>
