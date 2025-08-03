---
layout: default
layoutClass: gap-16
class: text-base
---

# On/Off Light Example (Router)

**Simple Zigbee on/off light implementation - [Zigbee_On_Off_Light](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_On_Off_Light)**

<div class="mt-4"></div>

### Sketch Configuration
- **Zigbee Mode** - Select if your device is a Coordinator/Router or End Device
- **Partition Scheme** - Select the partition scheme matching the Zigbee Mode

<div class="mt-1"></div>

````md magic-move {lines: true}
```cpp {*|1-2|3-7|8|*}
#include "Zigbee.h"

/* Zigbee light bulb configuration */
#define ZIGBEE_LIGHT_ENDPOINT 1
uint8_t led = RGB_BUILTIN;
uint8_t button = BOOT_PIN;

ZigbeeLight zbLight = ZigbeeLight(ZIGBEE_LIGHT_ENDPOINT);
```

```cpp {*}
void setLED(bool value) {
  digitalWrite(led, value);
}
```

```cpp {*|2|4-6|8-9}
void setup() {
  Serial.begin(115200);

  // Init LED and turn it OFF
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);

  // Init button for factory reset
  pinMode(button, INPUT_PULLUP);
```

```cpp {1-2|4-5|7-9}
  //Optional: set Zigbee device name and model
  zbLight.setManufacturerAndModel("Espressif", "ZBLightBulb");

  // Set callback function for light change
  zbLight.onLightChange(setLED);

  //Add endpoint to Zigbee Core
  Serial.println("Adding ZigbeeLight endpoint to Zigbee Core");
  Zigbee.addEndpoint(&zbLight);
```

```cpp {1-5|7-12|*}
  if (!Zigbee.begin(ZIGBEE_ROUTER)) {
    Serial.println("Zigbee failed to start!");
    Serial.println("Rebooting...");
    ESP.restart();
  }

  Serial.println("Connecting to network");
  while (!Zigbee.connected()) {
    Serial.print(".");
    delay(100);
  }
  Serial.println();
}
```

```cpp {*|2|3-12|8-10|14|*}
void loop() {
  if (digitalRead(button) == LOW) {  // Push button pressed
    delay(100);
    int startTime = millis();
    while (digitalRead(button) == LOW) {
      delay(50);
      if ((millis() - startTime) > 3000) {
        Serial.println("Resetting Zigbee to factory and rebooting in 1s.");
        delay(1000);
        Zigbee.factoryReset();
      }
    }

    zbLight.setLight(!zbLight.getLightState());
  }
  delay(100);
}
```
````
