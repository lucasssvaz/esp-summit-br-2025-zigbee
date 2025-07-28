---
layout: two-cols
layoutClass: gap-16
---

# Espressif Zigbee Support

**Select ESP32 series with IEEE 802.15.4 radio**

## Zigbee-Capable SoCs
- **ESP32-C6** - Wi-Fi 6 + Bluetooth 5 + IEEE 802.15.4
- **ESP32-C5** - Dual-band Wi-Fi 6 + Bluetooth 5 + IEEE 802.15.4
- **ESP32-H2** - Bluetooth 5 + IEEE 802.15.4 (no Wi-Fi)

## Gateway Solutions
- **Wi-Fi SoCs** (ESP32, ESP32-S3, ESP32-C3) + **Zigbee SoC** (ESP32-H2/C6)
- **UART connection** - Use Zigbee SoC as co-processor
- **Combined approach** - Wi-Fi gateway with dedicated Zigbee radio

## Key Features
- **IEEE 802.15.4 radio** - Native Zigbee support
- **Hardware acceleration** - AES encryption
- **Low power modes** - Battery operation
- **Rich peripherals** - GPIO, I2C, SPI, UART

::right::

<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Zigbee-Capable ESP32s</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-2 gap-3 text-xs">
        <div class="bg-blue-100 p-2 rounded">
          <div class="font-bold">ESP32-C6</div>
          <div>Single-core</div>
          <div>160MHz</div>
          <div class="text-green-600">✓ Zigbee</div>
        </div>
        <div class="bg-green-100 p-2 rounded">
          <div class="font-bold">ESP32-C5</div>
          <div>Single-core</div>
          <div>160MHz</div>
          <div class="text-green-600">✓ Zigbee</div>
        </div>
        <div class="bg-purple-100 p-2 rounded">
          <div class="font-bold">ESP32-H2</div>
          <div>Single-core</div>
          <div>96MHz</div>
          <div class="text-green-600">✓ Zigbee only</div>
        </div>
        <div class="bg-orange-100 p-2 rounded">
          <div class="font-bold">Co-Processor</div>
          <div>UART</div>
          <div>Connection</div>
          <div class="text-blue-600">Any ESP32</div>
        </div>
      </div>
      <div class="mt-3 text-xs text-gray-600">
        C6, C5, H2 have native support • Others use UART co-processor
      </div>
    </div>
  </div>
</div> 
