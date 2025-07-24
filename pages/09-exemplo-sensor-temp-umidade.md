---
layout: two-cols
layoutClass: gap-16
---

# Temperature/Humidity Sensor

**Battery-powered environmental sensor**

## Hardware Setup
- **ESP32-C3** - low power consumption
- **DHT22 sensor** - temperature & humidity
- **Li-ion battery** - 3.7V operation
- **Sleep mode** - power optimization

## Zigbee Features
- **End Device role** - battery powered
- **Temperature cluster** - standard reporting
- **Humidity cluster** - moisture sensing
- **Periodic reporting** - every 5 minutes

::right::

```cpp
#include <ZigbeeDevice.h>
#include <DHT.h>

ZigbeeDevice zigbee;
DHT dht(4, DHT22);

void setup() {
  dht.begin();
  
  zigbee.begin();
  zigbee.setDeviceRole(DEVICE_ROLE_END_DEVICE);
  
  // Create endpoint with sensors
  zigbee.createEndpoint(1, HA_PROFILE_ID, 
                       HA_TEMPERATURE_SENSOR_DEVICE_ID);
  zigbee.addCluster(1, CLUSTER_ID_TEMPERATURE, 
                   CLUSTER_SIDE_SERVER);
  zigbee.addCluster(1, CLUSTER_ID_HUMIDITY, 
                   CLUSTER_SIDE_SERVER);
}

void loop() {
  zigbee.loop();
  
  // Report every 5 minutes
  static unsigned long lastReport = 0;
  if (millis() - lastReport > 300000) {
    float temp = dht.readTemperature();
    float hum = dht.readHumidity();
    
    zigbee.setTemperature(temp);
    zigbee.setHumidity(hum);
    
    lastReport = millis();
  }
}
``` 
