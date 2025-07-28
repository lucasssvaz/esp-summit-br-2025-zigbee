---
layout: two-cols
layoutClass: gap-16
---

# Temperature/Humidity Sleepy Sensor

**Battery-powered environmental sensor**

## Hardware Setup
- **ESP32-H2/C6/C5** - low power consumption
- **Internal temp sensor** - ESP32 built-in sensor
- **Boot button** - factory reset (10s press)
- **Deep sleep mode** - 55s sleep cycles

## Zigbee Features
- **End Device role** - battery powered configuration
- **Measurement clusters** - temperature, humidity
- **Reporting cycle** - every 1 minute (55s sleep + 5s active)
- **Battery monitoring** - voltage and percentage reporting

::right::

```cpp
#include "Zigbee.h"

/* Zigbee temperature + humidity sensor configuration */
#define TEMP_SENSOR_ENDPOINT_NUMBER 10

#define uS_TO_S_FACTOR 1000000ULL /* Conversion factor for micro seconds to seconds */
#define TIME_TO_SLEEP  55         /* Sleep for 55s will + 5s delay for establishing connection => data reported every 1 minute */

uint8_t button = BOOT_PIN;

ZigbeeTempSensor zbTempSensor = ZigbeeTempSensor(TEMP_SENSOR_ENDPOINT_NUMBER);

/************************ Temp sensor *****************************/
void meausureAndSleep() {
  // Measure temperature sensor value
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

/********************* Arduino functions **************************/
void setup() {
  Serial.begin(115200);

  // Init button switch
  pinMode(button, INPUT_PULLUP);

  // Configure the wake up source and set to wake up every 5 seconds
  esp_sleep_enable_timer_wakeup(TIME_TO_SLEEP * uS_TO_S_FACTOR);

  // Optional: set Zigbee device name and model
  zbTempSensor.setManufacturerAndModel("Espressif", "SleepyZigbeeTempSensor");

  // Set minimum and maximum temperature measurement value (10-50°C is default range for chip temperature measurement)
  zbTempSensor.setMinMaxValue(10, 50);

  // Set tolerance for temperature measurement in °C (lowest possible value is 0.01°C)
  zbTempSensor.setTolerance(1);

  // Set power source to battery, battery percentage and battery voltage (now 100% and 3.5V for demonstration)
  // The value can be also updated by calling zbTempSensor.setBatteryPercentage(percentage) or zbTempSensor.setBatteryVoltage(voltage) anytime after Zigbee.begin()
  zbTempSensor.setPowerSource(ZB_POWER_SOURCE_BATTERY, 100, 35);

  // Add humidity cluster to the temperature sensor device with min, max and tolerance values
  zbTempSensor.addHumiditySensor(0, 100, 1);

  // Add endpoint to Zigbee Core
  Zigbee.addEndpoint(&zbTempSensor);

  // Create a custom Zigbee configuration for End Device with keep alive 10s to avoid interference with reporting data
  esp_zb_cfg_t zigbeeConfig = ZIGBEE_DEFAULT_ED_CONFIG();
  zigbeeConfig.nwk_cfg.zed_cfg.keep_alive = 10000;

  // For battery powered devices, it can be better to set timeout for Zigbee Begin to lower value to save battery
  // If the timeout has been reached, the network channel mask will be reset and the device will try to connect again after reset (scanning all channels)
  Zigbee.setTimeout(10000);  // Set timeout for Zigbee Begin to 10s (default is 30s)

  // When all EPs are registered, start Zigbee in End Device mode
  if (!Zigbee.begin(&zigbeeConfig, false)) {
    Serial.println("Zigbee failed to start!");
    Serial.println("Rebooting...");
    ESP.restart();  // If Zigbee failed to start, reboot the device and try again
  }
  Serial.println("Connecting to network");
  while (!Zigbee.connected()) {
    Serial.print(".");
    delay(100);
  }
  Serial.println();
  Serial.println("Successfully connected to Zigbee network");

  // Delay approx 1s (may be adjusted) to allow establishing proper connection with coordinator, needed for sleepy devices
  delay(1000);
}

void loop() {
  // Checking button for factory reset
  if (digitalRead(button) == LOW) {  // Push button pressed
    // Key debounce handling
    delay(100);
    int startTime = millis();
    while (digitalRead(button) == LOW) {
      delay(50);
      if ((millis() - startTime) > 10000) {
        // If key pressed for more than 10secs, factory reset Zigbee and reboot
        Serial.println("Resetting Zigbee to factory and rebooting in 1s.");
        delay(1000);
        // Optional set reset in factoryReset to false, to not restart device after erasing nvram, but set it to endless sleep manually instead
        Zigbee.factoryReset(false);
        Serial.println("Going to endless sleep, press RESET button or power off/on the device to wake up");
        esp_sleep_disable_wakeup_source(ESP_SLEEP_WAKEUP_TIMER);
        esp_deep_sleep_start();
      }
    }
  }

  // Call the function to measure temperature and put the device to sleep
  meausureAndSleep();
}
``` 
