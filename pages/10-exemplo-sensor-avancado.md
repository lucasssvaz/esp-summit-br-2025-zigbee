---
layout: two-cols
layoutClass: gap-16
---

# HVAC Boiler Control System

**Multi-endpoint device with boiler switch and monitoring sensors**

## Hardware Components
- **ESP32-C6/C5/H2** - Zigbee router device
- **Flow sensor** - water flow measurement
- **Pressure sensor** - system pressure monitoring

## Multi-Endpoint Design
- **Endpoint 1** - binary output (boiler switch control)
- **Endpoint 2** - flow sensor (0-100 m³/h range)
- **Endpoint 3** - pressure sensor (0-10000 hPa range)

## Features
- **Router role** - always-on mains powered device
- **Boot button** - factory reset (3s press) or instant data report
- **Real-time monitoring** - 2-second sensor reading cycle
- **HVAC integration** - boiler control with callback function
- **Configurable tolerance** - flow (1.0 m³/h) and pressure (1 hPa)


::right::

```cpp
#include "Zigbee.h"

uint8_t button = BOOT_PIN;

ZigbeeBinary zbBinary = ZigbeeBinary(1);
ZigbeeFlowSensor zbFlowSensor = ZigbeeFlowSensor(2);
ZigbeePressureSensor zbPressureSensor = ZigbeePressureSensor(3);

void onBoilerSwitch(bool state) {
  Serial.println("Boiler switch changed to: " + String(state));
  // Handle turning on/off the boiler
}

void setup() {
  Serial.begin(115200);

  // Init button switch
  pinMode(BOOT_PIN, INPUT_PULLUP);

  // Setup boiler switch
  zbBinary.setManufacturerAndModel("Espressif", "ZigbeeBoiler");
  zbBinary.addBinaryOutput();
  zbBinary.setBinaryOutputApplication(BINARY_OUTPUT_APPLICATION_TYPE_HVAC_BOILER);
  zbBinary.setBinaryOutputDescription("Boiler switch");
  zbBinary.onBinaryOutputChange(onBoilerSwitch);

  // Setup sensors
  zbFlowSensor.setMinMaxValue(0.0, 100.0); // Set minimum and maximum flow measurement value in 0,1 m3/h
  zbFlowSensor.setTolerance(1.0); // Set tolerance for flow measurement in 0,1 m3/h
  zbPressureSensor.setMinMaxValue(0, 10000); // Set minimum and maximum pressure measurement value in hPa
  zbPressureSensor.setTolerance(1); // Set tolerance for pressure measurement in hPa

  // Add endpoints to Zigbee Core
  Zigbee.addEndpoint(&zbBinary);
  Zigbee.addEndpoint(&zbFlowSensor);
  Zigbee.addEndpoint(&zbPressureSensor);

  Serial.println("Starting Zigbee...");
  // When all EPs are registered, start Zigbee in End Device mode
  if (!Zigbee.begin(ZIGBEE_ROUTER)) {
    Serial.println("Zigbee failed to start!");
    Serial.println("Rebooting...");
    ESP.restart();
  } else {
    Serial.println("Zigbee started successfully!");
  }
  Serial.println("Connecting to network");
  while (!Zigbee.connected()) {
    Serial.print(".");
    delay(100);
  }
  Serial.println();
}

void loop() {
  static uint32_t timeCounter = 0;

  // Read flow and pressure sensors every 2s
  if (!(timeCounter++ % 20)) {  // delaying for 100ms x 20 = 2s
    float flow_value = readFlowSensor();
    uint16_t pressure_value = readPressureSensor();
    Serial.printf("Updating flow sensor value to %.2f m3/h\r\n", flow_value);
    zbFlowSensor.setFlow(flow_value);
    Serial.printf("Updating pressure sensor value to %d hPa\r\n", pressure_value);
    zbPressureSensor.setPressure(pressure_value);
  }

  // Checking button for factory reset and reporting
  if (digitalRead(button) == LOW) {  // Push button pressed
    // Key debounce handling
    delay(100);
    int startTime = millis();
    while (digitalRead(button) == LOW) {
      delay(50);
      if ((millis() - startTime) > 3000) {
        // If key pressed for more than 3secs, factory reset Zigbee and reboot
        Serial.println("Resetting Zigbee to factory and rebooting in 1s.");
        delay(1000);
        Zigbee.factoryReset();
      }
    }
    zbFlowSensor.report();
    zbPressureSensor.report();
  }
  delay(100);
}

}
``` 
