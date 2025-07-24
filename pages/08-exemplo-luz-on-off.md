---
layout: two-cols
layoutClass: gap-16
---

# On/Off Light Example

**Simple Zigbee light switch implementation**

## Key Components
- **ESP32** - any model works
- **Relay module** - controls light
- **Zigbee End Device** - battery powered
- **On/Off cluster** - standard light control

## Features
- **Battery powered** - long life operation
- **Sleep mode** - power optimization
- **Instant response** - < 100ms latency
- **Home Assistant ready** - auto-discovery

::right::

```cpp
#include <ZigbeeDevice.h>

ZigbeeDevice zigbee;
const int RELAY_PIN = 2;

void setup() {
  pinMode(RELAY_PIN, OUTPUT);
  
  zigbee.begin();
  zigbee.setDeviceRole(DEVICE_ROLE_END_DEVICE);
  
  // Create endpoint with On/Off cluster
  zigbee.createEndpoint(1, HA_PROFILE_ID, 
                       HA_ON_OFF_LIGHT_DEVICE_ID);
  zigbee.addCluster(1, CLUSTER_ID_ON_OFF, 
                   CLUSTER_SIDE_SERVER);
}

void loop() {
  zigbee.loop();
  
  // Handle On/Off commands
  if (zigbee.isOnOffCommand()) {
    bool state = zigbee.getOnOffState();
    digitalWrite(RELAY_PIN, state);
  }
}
``` 
