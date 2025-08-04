---
# You can also start simply with 'default'
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
# background: https://cover.sli.dev
# favicon, can be a local file path or URL
favicon: '/favicons/favicon-32x32.png'
# force color schema for the slides, can be 'auto', 'light', or 'dark'
colorSchema: light
# aspect ratio for the slides
aspectRatio: 16/9
# real width of the canvas, unit in px
canvasWidth: 980
# some information about your slides (markdown enabled)
title: Zigbee com Arduino
info: |
  ## Zigbee com Arduino: conectando seus dispositivos ao Home Assistant
  Apresentação sobre o uso da biblioteca Zigbee integrada da Espressif com Arduino.

  [@lucasssvaz](https://github.com/lucasssvaz)
# apply unocss classes to the current slide
class: text-center text-base
# https://sli.dev/features/drawing
drawings:
  persist: false
# slide transition: https://sli.dev/guide/animations.html#slide-transitions
transition: slide-left
# enable MDC Syntax: https://sli.dev/features/mdc
mdc: true
# open graph
# seoMeta:
#  ogImage: https://cover.sli.dev
# Config required for slidev-component-poll addon
pollSettings:
  anonymous: true
---

# Zigbee com Arduino

<span style="font-size: 2rem;">Conectando seus dispositivos ao Home Assistant</span>

<div style="position: absolute; bottom: 2rem; left: 0; width: 100%; text-align: center;">
  Lucas Saavedra Vaz<br>
  <span style="font-size: 0.8rem; display: inline-block;">2025-08-05</span>
</div>

<!--
Esta apresentação aborda como usar a biblioteca Zigbee incluída no Arduino Core da Espressif para criar dispositivos que se integram perfeitamente ao Home Assistant.
-->

---
src: ./pages/01-introducao-zigbee.md
hide: false
---

---
src: ./pages/02-vantagens-zigbee.md
hide: false
---

---
src: ./pages/03-device-roles.md
hide: false
---

---
src: ./pages/04-espressif-zigbee-socs.md
hide: false
---

---
src: ./pages/05-espressif-zigbee-limitations.md
hide: false
---

---
src: ./pages/06-arduino-zigbee-library.md
hide: false
---

---
src: ./pages/07-zigbee-endpoints-clusters.md
hide: false
---

---
src: ./pages/08-exemplo-luz-on-off.md
hide: false
---

---
src: ./pages/09-exemplo-sensor-temp-umidade.md
hide: false
---

---
src: ./pages/10-exemplo-sensor-avancado.md
hide: false
---

---
src: ./pages/11-home-assistant-integration.md
hide: false
---

---
src: ./pages/12-device-discovery-setup.md
hide: false
---

---
src: ./pages/13-live-demo-showcase.md
hide: false
---

---
layout: center
class: text-center
---

# Obrigado!

## Perguntas e Discussão

<div style="margin-top: 2rem;">
  <div style="font-size: 1.2rem; margin-bottom: 1rem;">
    Vamos construir dispositivos Zigbee juntos!
  </div>
  <div style="font-size: 0.9rem; color: #666;">
    ESP32 + Arduino + Zigbee + Home Assistant
  </div>
</div>

<div style="margin-top: 3rem;">
  <div style="font-size: 1rem; margin-bottom: 1rem;">
    <strong>Recursos e Links</strong>
  </div>
  <div style="display: flex; justify-content: center; gap: 2rem; flex-wrap: wrap;">
    <div style="text-align: center;">
      <a href="https://docs.espressif.com/projects/arduino-esp32/en/latest/zigbee/zigbee.html" target="_blank" style="color: #007acc; text-decoration: none;">
        📚 Documentação Zigbee
      </a>
    </div>
    <div style="text-align: center;">
      <a href="https://github.com/espressif/arduino-esp32" target="_blank" style="color: #007acc; text-decoration: none;">
        🔧 Repositório arduino-esp32
      </a>
    </div>
    <div style="text-align: center;">
      <a href="https://github.com/lucasssvaz" target="_blank" style="color: #007acc; text-decoration: none;">
        👨‍💻 @lucasssvaz no GitHub
      </a>
    </div>
  </div>
</div>
