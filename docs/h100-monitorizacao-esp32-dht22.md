# Monitorização ambiental Hyundai H100 — ESP32 + DHT22

Estado em 29-10-2026: protótipo COMCS PL6 validado; instalação definitiva na carrinha pendente.

## Objetivo e arquitetura

O ESP32 próprio, instalado na carrinha, lê um DHT22 e usa o hotspot do telemóvel quando este estiver ativo. Publica temperatura e humidade por MQTT/TLS no EMQX Cloud. Em casa, o Raspberry Pi 5 executará Node-RED e o dashboard, acessível no telemóvel ou computador via Tailscale.

```text
DHT22 -> ESP32 -> hotspot do telemóvel -> EMQX Cloud (MQTT/TLS)
                                           |
                                           v
                               Raspberry Pi 5 (Node-RED)
                                           |
                                           v
                              Dashboard (PC/telemóvel)
                                  acesso via Tailscale
```

Tailscale protege o acesso ao Raspberry Pi; o ESP32 comunica diretamente com o broker EMQX.

## Material

| Item | Estado | Recomendação |
| --- | --- | --- |
| ESP32 | Já disponível | Confirmar modelo e GPIO |
| **DHT22 / AM2302** | **Comprar** | Preferir módulo de 3 pinos, compatível com 3,3 V; melhor precisão típica que DHT11 |
| Cabos Dupont | Verificar | Para ligação sensor/ESP32 |
| USB + fonte de 5 V | Verificar | Alimentação estável, sem descarga indevida da bateria |
| Caixa ventilada | Recomendado | Proteção mecânica sem bloquear o sensor |
| Resistência 4,7–10 kΩ | Se necessário | Pull-up de DATA para 3,3 V em sensor sem resistência integrada |
| OLED I²C 0,96 polegadas | Opcional | Leitura local na carrinha |

Confirmar sempre a pinagem do módulo adquirido. Como alternativa futura de maior qualidade, avaliar SHT31 ou BME280.

## Protótipo validado — COMCS PL6

- ESP32-S3 com DHT11 da aula publica por MQTT/TLS (porta 8883).
- Tópicos: `comcs/pl6/temperature`, `comcs/pl6/humidity`, `comcs/pl6/heatindex`.
- Node-RED 5 com FlowFuse Dashboard 2 no Ubuntu recebe as mensagens do EMQX Cloud.
- Dashboard com indicadores de temperatura e humidade, consultado também no telemóvel.
- Leituras observadas: 22,6 °C e 48% (exemplo pontual, não histórico).
- Para a carrinha, criar tópicos próprios: `van/h100/temperature`, `van/h100/humidity`, `van/h100/status`.

## Próximas tarefas

1. Comprar DHT22/AM2302 e confirmar o ESP32 próprio.
2. Ligar o sensor e adaptar firmware com reconexão Wi-Fi/MQTT, TLS validado e tópicos da carrinha.
3. Verificar `sudo docker ps` no Raspberry Pi 5 (Docker e Compose instalados; acesso requer sudo).
4. Instalar Node-RED em container Docker separado do Nextcloud, com dados persistentes e reinício automático.
5. Exportar o flow do Ubuntu, importar no Raspberry Pi, reconfigurar credenciais e testar o dashboard via Tailscale.
6. Adicionar indicador offline/última medição; considerar armazenamento de histórico e alertas.
7. Testar alimentação elétrica e posicionamento do sensor na carrinha, longe de sol direto e saídas de ar.

## Segurança e limitações

- Nunca guardar passwords, `secrets.h`, tokens ou certificados privados no Git.
- Validar certificado TLS do broker e configurar autenticação/ACL MQTT.
- Não expor a interface de administração do Node-RED à Internet pública; proteger o editor e usar Tailscale.
- Sem hotspot ativo, o ESP32 não transmite e o dashboard não recebe novas medições. O Raspberry Pi pode continuar a servir o dashboard, mas precisa de guardar histórico para mostrar dados anteriores.
