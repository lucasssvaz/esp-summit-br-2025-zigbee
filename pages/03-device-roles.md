---
layout: two-cols
layoutClass: gap-16
class: text-base
---

# Funções dos Dispositivos Zigbee

**Três tipos de dispositivos em uma rede Zigbee**

<div class="mt-4"></div>

### Coordinator
- **Gerenciador da rede** - Forma a rede
- **Sempre ligado** - Conectado à rede elétrica
- **Único na rede** - Ponto de entrada
- **Armazena informações da rede** - Chaves de segurança

<div class="mt-4"></div>

### Router
- **Retransmissor de dados** - Estende o alcance da rede
- **Sempre escutando** - Alimentado pela rede elétrica
- **Múltiplos permitidos** - Peça central da rede mesh
- **Pode conectar dispositivos** - Função de pai

::right::

### End Device
- **Alimentado por bateria** - Modo de sleep
- **Alcance limitado** - Conexão direta
- **Operação simples** - Sensores/atuadores
- **Dependente do pai** - Router/coordinator

<div class="grid grid-cols-1 gap-4 mt-2">
  <div class="text-center">
    <div class="bg-gray-100 p-4 rounded-lg">
      <div class="flex flex-col items-center space-y-3">
        <div class="w-12 h-12 bg-blue-600 rounded-full flex items-center justify-center text-white font-bold">C</div>
        <div class="text-xs text-gray-600">Coordinator</div>
        <div class="w-1 h-4 bg-gray-400"></div>
        <div class="flex space-x-4">
          <div class="w-10 h-10 bg-green-600 rounded-full flex items-center justify-center text-white font-bold">R</div>
          <div class="w-10 h-10 bg-green-600 rounded-full flex items-center justify-center text-white font-bold">R</div>
        </div>
        <div class="text-xs text-gray-600">Routers</div>
        <div class="w-1 h-4 bg-gray-400"></div>
        <div class="flex space-x-2">
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
          <div class="w-8 h-8 bg-orange-500 rounded-full flex items-center justify-center text-white text-xs">E</div>
        </div>
        <div class="text-xs text-gray-600">End Devices</div>
      </div>
    </div>
  </div>
</div> 
