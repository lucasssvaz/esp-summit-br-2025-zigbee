---
layout: default
layoutClass: gap-16
---

# Temperature/Humidity Sleepy Sensor (ED)

**Battery-powered environmental sensor - [Zigbee_Temp_Hum_Sensor_Sleepy](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_Temp_Hum_Sensor_Sleepy)**

````md magic-move {lines: true}
```cpp {*|3-7|11|*}
#include "Zigbee.h"

/* Zigbee temperature + humidity sensor configuration */
#define TEMP_SENSOR_ENDPOINT_NUMBER 10

#define uS_TO_S_FACTOR 1000000ULL /* Conversion factor for micro seconds to seconds */
#define TIME_TO_SLEEP  55         /* Sleep 55s + 5s delay for connection => data reported every 1 minute */

uint8_t button = BOOT_PIN;

ZigbeeTempSensor zbTempSensor = ZigbeeTempSensor(TEMP_SENSOR_ENDPOINT_NUMBER);
```

```cpp {*|2-6|8-10|12-18|19-21|*}
void measureAndSleep() {
  // Measure internal CPU temperature
  float temperature = temperatureRead();

  // Use temperature value as humidity value to demonstrate both temperature and humidity
  float humidity = temperature;

  // Update temperature and humidity values in Temperature sensor EP
  zbTempSensor.setTemperature(temperature);
  zbTempSensor.setHumidity(humidity);

  // Report temperature and humidity values
  zbTempSensor.report();
  Serial.printf("Reported temperature: %.2f°C, Humidity: %.2f%%\r\n", temperature, humidity);

  // Add small delay to allow the data to be sent before going to sleep
  delay(100);

  // Put device to deep sleep
  Serial.println("Going to sleep now");
  esp_deep_sleep_start();
}
```

```cpp {*|2-3|5-6|8-9|11-12|14-15|17-18|20-21}
void setup() {
  Serial.begin(115200);
  pinMode(button, INPUT_PULLUP);

  // Configure the wake up source and set to wake up every 55 seconds
  esp_sleep_enable_timer_wakeup(TIME_TO_SLEEP * uS_TO_S_FACTOR);

  // Set minimum and maximum temperature measurement value
  zbTempSensor.setMinMaxValue(10, 50);

  // Set tolerance/precision for temperature measurement in °C
  zbTempSensor.setTolerance(1);

  // Set power source to battery, battery percentage and battery voltage (now 100% and 3.5V for demonstration)
  zbTempSensor.setPowerSource(ZB_POWER_SOURCE_BATTERY, 100, 35);

  // Add humidity cluster to the temperature sensor device with min, max and tolerance values
  zbTempSensor.addHumiditySensor(0, 100, 1);

  Serial.println("Adding ZigbeeTempSensor endpoint to Zigbee Core");
  Zigbee.addEndpoint(&zbTempSensor);
```

```cpp {1-3|5-6|8-17|19-20|*}
  // Create a custom Zigbee configuration for ED with keep alive 10s to avoid issues with reporting data
  esp_zb_cfg_t zigbeeConfig = ZIGBEE_DEFAULT_ED_CONFIG();
  zigbeeConfig.nwk_cfg.zed_cfg.keep_alive = 10000;

  // For battery powered devices, it can be better to set timeout for Zigbee Begin to lower value to save battery
  Zigbee.setTimeout(10000);  // Set timeout for Zigbee Begin to 10s (default is 30s)

  if (!Zigbee.begin(&zigbeeConfig, false)) {
    Serial.println("Zigbee failed to start!");
    Serial.println("Rebooting...");
    ESP.restart();  // If Zigbee failed to start, reboot the device and try again
  }
  Serial.println("Connecting to network");
  while (!Zigbee.connected()) {
    delay(100);
  }
  Serial.println("Successfully connected to Zigbee network");

  // Delay approx 1s to allow establishing proper connection with coordinator, needed for sleepy devices
  delay(1000);
}
```

```cpp {*|5|*}
void loop() {
  // ... Same as previous example ...

  // Call the function to measure temperature and put the device to sleep
  measureAndSleep();
}
```
```` 
