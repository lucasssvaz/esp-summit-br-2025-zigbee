---
layout: default
layoutClass: gap-16
---

# Dispositivo Multi-Endpoint

**Múltiplos sensores/switches em um dispositivo - [Zigbee_Pressure_Flow_Sensor](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_Pressure_Flow_Sensor)**

```cpp {*|1-3|8-10|18-19|*}
ZigbeeBinary zbBinary = ZigbeeBinary(1);                         // Switch (Saída)
ZigbeeFlowSensor zbFlowSensor = ZigbeeFlowSensor(2);             // Sensor de Fluxo (Entrada)
ZigbeePressureSensor zbPressureSensor = ZigbeePressureSensor(3); // Sensor de Pressão (Entrada)

void setup() {
  // ... resto do código ...

  Zigbee.addEndpoint(&zbBinary);
  Zigbee.addEndpoint(&zbFlowSensor);
  Zigbee.addEndpoint(&zbPressureSensor);

  // ... resto do código ...
}

void loop() {
  // ... resto do código ...

  zbFlowSensor.report();
  zbPressureSensor.report();

  // ... resto do código ...
}
``` 
