---
layout: two-cols
layoutClass: gap-16
---

# Endpoints Zigbee

**Blocos de construção para funcionalidade do dispositivo**

## Classes de Endpoints
- **Interfaces virtuais** - Até 240 por dispositivo
- **Funções independentes** - Cada uma serve um propósito específico
- **Grupos de clusters** - Funcionalidades relacionadas agrupadas
- **Identificação do dispositivo** - Perfil e IDs de dispositivo

::right::

<div class="grid grid-cols-1 gap-4 mt-12">
  <div class="text-center">
    <h3 class="text-lg font-semibold mb-2">Exemplos de Endpoints</h3>
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="grid grid-cols-2 gap-2 text-xs">
        <div class="bg-blue-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Básicos</div>
          <div>I/O binário, analógico, multistate</div>
        </div>
        <div class="bg-green-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Interruptores</div>
          <div>Liga/desliga, dimmer, tomada, interruptor de contato</div>
        </div>
        <div class="bg-purple-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Lâmpadas</div>
          <div>Liga/desliga, dimmer, dimmer de cor</div>
        </div>
        <div class="bg-orange-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Controladores</div>
          <div>Termostato, controle de ventilador</div>
        </div>
        <div class="bg-red-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Sensores</div>
          <div>Temperatura, umidade, CO2, iluminância</div>
        </div>
        <div class="bg-yellow-100 p-2 rounded flex flex-col justify-center">
          <div class="font-bold">Outros</div>
          <div>Gateway, extensor de alcance</div>
        </div>
      </div>
    </div>
  </div>
</div> 

- Para mais informações e outros endpoints, consulte a [documentação](https://docs.espressif.com/projects/arduino-esp32/en/latest/zigbee/zigbee.html).
