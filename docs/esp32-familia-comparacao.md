# Família ESP32 — comparação para a Hyundai H100

Data: 2026-11-02. Estado: nota de estudo e avaliação; nenhuma compra ou migração decidida.

## Origem
Imagem de divulgação da conta circuit_digest: «5 ESP32 Controllers You Should Know in 2026». As categorias da imagem são simplificações de marketing, não requisitos nem recomendações técnicas verificadas.

| SoC | Características relevantes | Possível uso na H100 |
| --- | --- | --- |
| ESP32-C5 | Wi-Fi 6 dual-band (2,4/5 GHz), BLE | Telemetria com redes de 5 GHz |
| ESP32-C6 | Wi-Fi 6 2,4 GHz, BLE, IEEE 802.15.4 (Thread/Zigbee) | Sensores e rede domótica |
| ESP32-S3 | Dois núcleos Xtensa LX7, Wi-Fi 2,4 GHz, BLE, USB OTG | Firmware de sensores, dashboard local, processamento |
| ESP32-P4 | Processador de aplicação de maior capacidade, interfaces multimédia; **sem rádio Wi-Fi/Bluetooth integrado** | Display e HMI com módulo de conectividade externo |
| ESP32-C61 | Wi-Fi 6 2,4 GHz, BLE; opção económica | Nó de telemetria |

## Relação com o projeto existente
O protótipo **COMCS PL6** já foi validado com **ESP32-S3 + DHT11 + MQTT/TLS**. O plano de instalação na H100 está em [h100-monitorizacao-esp32-dht22.md](h100-monitorizacao-esp32-dht22.md): sensor DHT22, hotspot do telemóvel, EMQX Cloud, Node-RED no Raspberry Pi e acesso por Tailscale.

**Decisão atual:** manter o ESP32 já disponível e a arquitetura validada. Não trocar de MCU por causa de uma publicação nas redes sociais.

## Critérios para eventual escolha futura
1. Requisitos funcionais: sensores, GPIO, ADC, interfaces I²C/SPI/UART, display.
2. Rede: hotspot Wi-Fi 2,4/5 GHz, BLE, eventual Thread/Zigbee.
3. Consumo e alimentação: funcionamento com motor desligado, sleep, proteção automóvel e orçamento energético.
4. Recursos de firmware: RAM/flash, FreeRTOS, TLS, OTA e debugging.
5. Custo, disponibilidade, suporte ESP-IDF e ciclo de vida.

## Referências oficiais para consulta antes de decidir
- [Espressif — ESP32-S3](https://www.espressif.com/en/products/socs/esp32-s3)
- [Espressif — ESP32-C6](https://www.espressif.com/en/products/socs/esp32-c6)
- [Espressif — ESP32-C5](https://www.espressif.com/en/products/socs/esp32-c5)
- [Espressif — ESP32-P4](https://www.espressif.com/en/products/socs/esp32-p4)
- [Espressif — ESP32-C61](https://www.espressif.com/en/products/socs/esp32-c61)

Nota: SoC, módulo e placa de desenvolvimento não são a mesma coisa; verificar pinagem e periféricos da placa concreta.
