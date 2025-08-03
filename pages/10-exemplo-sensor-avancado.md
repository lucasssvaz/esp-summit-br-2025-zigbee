---
layout: default
layoutClass: gap-16
---

# Multi-Endpoint Device

**Multiple sensors/switches in one device - [Zigbee_Pressure_Flow_Sensor](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_Pressure_Flow_Sensor)**

```cpp {*|1-3|8-10|18-19|*}
ZigbeeBinary zbBinary = ZigbeeBinary(1);                         // Switch (Output)
ZigbeeFlowSensor zbFlowSensor = ZigbeeFlowSensor(2);             // Flow Sensor (Input)
ZigbeePressureSensor zbPressureSensor = ZigbeePressureSensor(3); // Pressure Sensor (Input)

void setup() {
  // ... other code ...

  Zigbee.addEndpoint(&zbBinary);
  Zigbee.addEndpoint(&zbFlowSensor);
  Zigbee.addEndpoint(&zbPressureSensor);

  // ... other code ...
}

void loop() {
  // ... other code ...

  zbFlowSensor.report();
  zbPressureSensor.report();

  // ... other code ...
}
``` 
