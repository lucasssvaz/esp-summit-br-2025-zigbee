---
layout: default
layoutClass: gap-16
class: text-base
---

# Exemplo de Luz On/Off (Router)

**Implementação simples de luz Zigbee com liga/desliga - [Zigbee_On_Off_Light](https://github.com/espressif/arduino-esp32/tree/master/libraries/Zigbee/examples/Zigbee_On_Off_Light)**

<div class="mt-4"></div>

### Configuração do Sketch
- **Zigbee Mode** - Selecione se seu dispositivo é um Coordinator/Router ou End Device
- **Partition Scheme** - Selecione o esquema de partição correspondente ao Zigbee Mode

<div class="mt-1"></div>

````md magic-move {lines: true}
```cpp {*|1-2|3-7|8|*}
#include "Zigbee.h"

/* Configuração da lâmpada Zigbee */
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

  // Inicializa LED e desliga
  pinMode(led, OUTPUT);
  digitalWrite(led, LOW);

  // Inicializa botão para reset de fábrica
  pinMode(button, INPUT_PULLUP);
```

```cpp {1-2|4-5|7-9}
  // Opcional: define nome e modelo do dispositivo Zigbee
  zbLight.setManufacturerAndModel("Espressif", "ZBLightBulb");

  // Define função de callback para mudança de luz
  zbLight.onLightChange(setLED);

  // Adiciona endpoint ao Zigbee Core
  Serial.println("Adicionando endpoint ZigbeeLight ao Zigbee Core");
  Zigbee.addEndpoint(&zbLight);
```

```cpp {1-5|7-12|*}
  if (!Zigbee.begin(ZIGBEE_ROUTER)) {
    Serial.println("Zigbee falhou ao iniciar!");
    Serial.println("Reiniciando...");
    ESP.restart();
  }

  Serial.println("Conectando à rede");
  while (!Zigbee.connected()) {
    Serial.print(".");
    delay(100);
  }
  Serial.println();
}
```

```cpp {*|2|3-12|8-10|14|*}
void loop() {
  if (digitalRead(button) == LOW) {  // Botão pressionado
    delay(100);
    int startTime = millis();
    while (digitalRead(button) == LOW) {
      delay(50);
      if ((millis() - startTime) > 3000) {
        Serial.println("Resetando Zigbee para configuração de fábrica e reiniciando em 1s.");
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
