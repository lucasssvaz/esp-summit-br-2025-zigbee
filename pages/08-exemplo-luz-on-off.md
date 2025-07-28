---
layout: two-cols
layoutClass: gap-16
---

# On/Off Light Example

**Simple Zigbee on/off light implementation**

## Key Components
- **ESP32-C6/C5/H2** - native support of Zigbee
- **Built-in RGB LED** - uses RGB_BUILTIN pin
- **Boot button** - for factory reset and manual toggle
- **ZigbeeLight endpoint** - implements On/Off light cluster

## Features
- **Factory reset** - 3-second button press
- **Manual control** - button toggle functionality
- **Auto-discovery** - standard Zigbee HA profile
- **Network joining** - automatic coordinator discovery

## Important
- **Zigbee Mode** - for router mode choose "Zigbee ZCZR (coordinator/router)"
- **Partition Scheme** - for router mode select "Zigbee ZCZR xMB with spiffs"

::right::

```cpp
#include "Zigbee.h"

/* Zigbee light bulb configuration */
#define ZIGBEE_LIGHT_ENDPOINT 1
uint8_t led = RGB_BUILTIN;
uint8_t button = BOOT_PIN;

ZigbeeLight zbLight = ZigbeeLight(ZIGBEE_LIGHT_ENDPOINT);

/********************* RGB LED functions **************************/
void setLED(bool value) {
  digitalWrite(led, value);
}

/********************* Arduino functions **************************/
void setup() {
  Serial.begin(115200);

  // Init LED and turn it OFF (if LED_PIN == RGB_BUILTIN, the rgbLedWrite() will be used under the hood)
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);

  // Init button for factory reset
  pinMode(button, INPUT_PULLUP);

  //Optional: set Zigbee device name and model
  zbLight.setManufacturerAndModel("Espressif", "ZBLightBulb");

  // Set callback function for light change
  zbLight.onLightChange(setLED);

  //Add endpoint to Zigbee Core
  Serial.println("Adding ZigbeeLight endpoint to Zigbee Core");
  Zigbee.addEndpoint(&zbLight);

  // When all EPs are registered, start Zigbee in router role.
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

void loop() {
  // Checking button for factory reset
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
    // Toggle light by pressing the button
    zbLight.setLight(!zbLight.getLightState());
  }
  delay(100);
}

``` 
