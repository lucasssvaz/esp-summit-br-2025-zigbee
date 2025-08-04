---
layout: two-cols
layoutClass: gap-16
---

# Protocolo Zigbee

**Protocolo de rede mesh sem fio de baixo consumo**

- Frequência **2.4 GHz**
- Padrão **IEEE 802.15.4**
- **Rede mesh** - Dispositivos retransmitem dados
- **Baixa latência** - Resposta rápida
- **Interoperável** - Certificado pela Zigbee Alliance

<div class="mt-8"></div>
<div class="grid grid-cols-1 gap-4">
  <div class="text-center">
    <h5 class="text-lg font-semibold mb-2">Tipos de Nós Zigbee</h5>
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

<div class="flex items-start justify-center h-full -mt-8">
  <div class="scale-75">
    <ZigbeeGraph />
  </div>
</div>
