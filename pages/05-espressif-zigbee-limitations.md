---
layout: default
layoutClass: gap-16
class: text-base
---

# Limitações do Zigbee da Espressif

**Considerações importantes para desenvolvimento**

- **Alternância de rádio** - Necessário gerenciar WiFi/Zigbee. WiFi e Zigbee não podem funcionar ao mesmo tempo.
- **Gerenciamento de memória** - RAM limitada para redes grandes.
- **Otimização de energia** - Maior consumo de energia que chips dedicados a Zigbee. Requer uso eficaz dos modos de sleep.
- **Tamanho da rede** - Limite prático de ~50 dispositivos por coordinator.

<figure class="flex flex-col justify-center items-center">
  <img src="/images/esp-thread-border-router-board.png" alt="ESP Thread Border Router / Zigbee Gateway V1.2 Board" class="w-1/4" />
  <figcaption class="text-sm text-gray-600">ESP Thread Border Router / Zigbee Gateway V1.2</figcaption>
</figure>
