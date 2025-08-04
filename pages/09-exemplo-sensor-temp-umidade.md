---
layout: default
layoutClass: gap-16
---

# Sensor de Temp./Umidade com Sleep (ED)

**Sensor de ambiente alimentado por bateria - [Zigbee_Temp_Hum_Sensor_Sleepy](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_Temp_Hum_Sensor_Sleepy)**

````md magic-move {lines: true}
```cpp {*|3-7|11|*}
#include "Zigbee.h"

/* Configuração do sensor de temperatura + umidade Zigbee */
#define TEMP_SENSOR_ENDPOINT_NUMBER 10

#define uS_TO_S_FACTOR 1000000ULL /* Fator de conversão de microssegundos para segundos */
#define TIME_TO_SLEEP  55         /* Sleep de 55+5s de atraso para conexão => dados reportados a cada 1 minuto */

uint8_t button = BOOT_PIN;

ZigbeeTempSensor zbTempSensor = ZigbeeTempSensor(TEMP_SENSOR_ENDPOINT_NUMBER);
```

```cpp {*|2-6|8-10|12-18|19-21|*}
void measureAndSleep() {
  // Mede temperatura interna da CPU
  float temperature = temperatureRead();

  // Usa valor de temperatura como valor de umidade para demonstrar temperatura e umidade
  float humidity = temperature;

  // Atualiza valores de temperatura e umidade no EP do sensor de temperatura
  zbTempSensor.setTemperature(temperature);
  zbTempSensor.setHumidity(humidity);

  // Reporta valores de temperatura e umidade
  zbTempSensor.report();
  Serial.printf("Temperatura reportada: %.2f°C, Umidade: %.2f%%\r\n", temperature, humidity);

  // Adiciona pequeno atraso para permitir que os dados sejam enviados antes do sleep
  delay(100);

  // Coloca dispositivo em deep sleep
  Serial.println("Entrando em deep sleep");
  esp_deep_sleep_start();
}
```

```cpp {*|2-3|5-6|8-9|11-12|14-16|18-19|21-22}
void setup() {
  Serial.begin(115200);
  pinMode(button, INPUT_PULLUP);

  // Configura o timer de despertar e define para acordar a cada 55 segundos
  esp_sleep_enable_timer_wakeup(TIME_TO_SLEEP * uS_TO_S_FACTOR);

  // Define valor mínimo e máximo de medição de temperatura
  zbTempSensor.setMinMaxValue(10, 50);

  // Define tolerância/precisão para medição de temperatura em °C
  zbTempSensor.setTolerance(1);

  // Define fonte de energia como bateria, porcentagem da bateria e tensão da bateria
  // (agora 100% e 3.5V para demonstração)
  zbTempSensor.setPowerSource(ZB_POWER_SOURCE_BATTERY, 100, 35);

  // Adiciona cluster de umidade ao dispositivo sensor de temperatura com valores min, max e tolerância
  zbTempSensor.addHumiditySensor(0, 100, 1);

  Serial.println("Adicionando endpoint ZigbeeTempSensor ao Zigbee Core");
  Zigbee.addEndpoint(&zbTempSensor);
```

```cpp {1-4|6-8|10-18|20-21|*}
  // Cria uma configuração Zigbee personalizada para ED com keep alive de 10s para
  // evitar problemas com o envio de dados
  esp_zb_cfg_t zigbeeConfig = ZIGBEE_DEFAULT_ED_CONFIG();
  zigbeeConfig.nwk_cfg.zed_cfg.keep_alive = 10000;

  // Para dispositivos alimentados por bateria, pode ser melhor definir timeout para
  // iniciar o Zigbee para um valor menor para economizar bateria
  Zigbee.setTimeout(10000);  // Define timeout para iniciar o Zigbee para 10s (padrão é 30s)

  if (!Zigbee.begin(&zigbeeConfig, false)) {
    Serial.println("Zigbee falhou ao iniciar!");
    Serial.println("Reiniciando...");
    ESP.restart();  // Se Zigbee falhou ao iniciar, reinicia o dispositivo e tenta novamente
  }
  while (!Zigbee.connected()) {
    delay(100);
  }
  Serial.println("Conectado com sucesso à rede Zigbee");

  // Atraso de 1s para permitir conexão adequada com coordinator, necessário para dispositivos com sleep
  delay(1000);
}
```

```cpp {*|5|*}
void loop() {
  // ... Mesmo que exemplo anterior ...

  // Chama a função para medir temperatura e colocar o dispositivo em sleep
  measureAndSleep();
}
```
```` 
