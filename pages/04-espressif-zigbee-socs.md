---
layout: default
layoutClass: gap-16 text-base
---

# Suporte Zigbee da Espressif

**Selecione os chips ESP32 com rádio IEEE 802.15.4**

<div class="grid grid-cols-1 gap-4 mt-12">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">SoCs com suporte a Zigbee</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-2 gap-3 text-xs">
        <div class="bg-blue-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">ESP32-C6</div>
          <div>Single-core</div>
          <div>160MHz</div>
          <div class="text-green-600">✓ Zigbee</div>
          <div class="text-blue-600">Wi-Fi 6 + BT5</div>
        </div>
        <div class="bg-green-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">ESP32-C5</div>
          <div>Single-core</div>
          <div>160MHz</div>
          <div class="text-green-600">✓ Zigbee</div>
          <div class="text-blue-600">Wi-Fi 6 Dual-band + BT5</div>
        </div>
        <div class="bg-purple-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">ESP32-H2</div>
          <div>Single-core</div>
          <div>96MHz</div>
          <div class="text-green-600">✓ Zigbee</div>
          <div class="text-blue-600">BT5 apenas (sem Wi-Fi)</div>
        </div>
        <div class="bg-orange-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Co-processador</div>
          <div>Conexão UART</div>
          <div class="text-blue-600">Qualquer ESP32</div>
        </div>
      </div>
      <div class="mt-3 text-xs text-gray-600">
        C6, C5, H2 têm suporte nativo IEEE 802.15.4 • Outros usam co-processador por UART
      </div>
    </div>
  </div>
</div> 
