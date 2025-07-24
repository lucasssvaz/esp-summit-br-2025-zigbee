---
layout: two-cols
layoutClass: gap-16
---

# Advanced Sensor Example

**Multi-cluster device with multiple sensors**

## Hardware Components
- **ESP32-S3** - dual-core processing
- **BME280** - pressure, temperature, humidity
- **PIR sensor** - motion detection
- **Light sensor** - ambient light level
- **RGB LED** - status indication

## Multi-Endpoint Design
- **Endpoint 1** - environmental sensors
- **Endpoint 2** - occupancy detection
- **Endpoint 3** - light level sensor
- **Endpoint 4** - RGB light control

::right::

```cpp
#include <ZigbeeDevice.h>
#include <Adafruit_BME280.h>

ZigbeeDevice zigbee;
Adafruit_BME280 bme;

void setup() {
  bme.begin();
  
  zigbee.begin();
  zigbee.setDeviceRole(DEVICE_ROLE_END_DEVICE);
  
  // Environmental endpoint
  zigbee.createEndpoint(1, HA_PROFILE_ID, 
                       HA_TEMPERATURE_SENSOR_DEVICE_ID);
  zigbee.addCluster(1, CLUSTER_ID_TEMPERATURE, 
                   CLUSTER_SIDE_SERVER);
  zigbee.addCluster(1, CLUSTER_ID_PRESSURE, 
                   CLUSTER_SIDE_SERVER);
  
  // Occupancy endpoint
  zigbee.createEndpoint(2, HA_PROFILE_ID, 
                       HA_OCCUPANCY_SENSOR_DEVICE_ID);
  zigbee.addCluster(2, CLUSTER_ID_OCCUPANCY, 
                   CLUSTER_SIDE_SERVER);
}

void loop() {
  zigbee.loop();
  
  // Report sensor data
  zigbee.setTemperature(bme.readTemperature());
  zigbee.setPressure(bme.readPressure() / 100);
  zigbee.setOccupancy(digitalRead(PIR_PIN));
}
``` 
