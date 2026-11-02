# Monitorização ambiental Hyundai H100 — ESP32 + DHT22

Estado em 02-11-2026: protótipo COMCS PL6 validado; hardware principal da V1 recebido; montagem de bancada ESP32 + DHT22 pendente.

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

## Alimentação prevista na carrinha — V1

A H100 já possui saída USB no sistema auxiliar. Para a primeira versão, a opção preferida é alimentar o ESP32 diretamente por USB, evitando adicionar um conversor DC-DC ajustável sem necessidade.

```text
Bateria auxiliar 12,8 V
        |
        v
painel USB existente na carrinha
(conversão para ~5 V)
        |
        v
      USB
        |
        v
      ESP32
        |
        +--> DHT22
        |
        +--> OLED I2C (fase seguinte)
```

Antes da instalação definitiva:

1. medir a saída USB com multímetro;
2. confirmar aproximadamente 5 V estáveis;
3. validar o ESP32 alimentado por essa porta;
4. só depois montar a eletrónica na caixa.

O conversor ajustável usado no projeto de rega não é necessário para esta V1 e não deve ser inserido no caminho de alimentação sem uma necessidade concreta.

## Material

| Item | Estado | Observações |
| --- | --- | --- |
| ESP32 DevKit | **2 unidades disponíveis** | Um para desenvolvimento/bancada e um para a carrinha |
| DHT22 / AM2302 | **2 unidades disponíveis** | Um para a carrinha e um de reserva/desenvolvimento |
| Breadboards pequenas | **Disponíveis** | Suficientes para o primeiro protótipo ESP32 + DHT22 |
| Placa perfurada ponto-a-ponto | **Disponível** | Para versão soldada depois da validação em breadboard |
| Bornes/terminais de parafuso | **Disponíveis** | Macho/fêmea; úteis para sensor removível e manutenção |
| Kit de fios | **Disponível** | Para prototipagem e interligações |
| Espaçadores | **Disponíveis** | Para fixação mecânica dentro da caixa |
| Caixas Pulsar | **Disponíveis** | Maiores do que o necessário para V1, mas com margem para expansão |
| Estação de soldadura + estanho | **Disponível** | Usar apenas depois de o circuito estar validado |
| Multímetro | **Disponível** | Necessário para validar alimentação |
| OLED I2C 0,96" | **Em falta / fase seguinte** | Preferência atual: SSD1306 128x64, 3,3 V |
| Resistência 4,7–10 kΩ | Verificar | Só necessária se o módulo DHT22 não tiver pull-up integrado |

Confirmar sempre a pinagem real do módulo DHT22 adquirido.

## Posicionamento do DHT22

O DHT22 não deve ficar fechado dentro da mesma caixa do ESP32 porque isso introduziria erro por aquecimento da eletrónica e ar estagnado.

Arquitetura pretendida:

```text
DHT22
  |
  | 3 fios: VCC / DATA / GND
  |
  v
borne removível
  |
  v
+-----------------------+
| caixa eletrónica      |
|                       |
| ESP32 + perfboard     |
| alimentação           |
+-----------------------+
```

O sensor fica:

- fora da caixa eletrónica;
- dentro do habitáculo;
- com circulação de ar;
- longe de sol direto;
- sem contacto direto com a chapa da carrinha;
- longe de saídas de ar quente/frio.

Para uma futura medição exterior deverá ser usado um sensor/encapsulamento adequado à exposição ambiental; não expor simplesmente o DHT22 interno à chuva ou condensação.

## Breadboard vs perfboard

### Breadboard

Usar para:

- montar;
- experimentar;
- alterar ligações;
- validar pinagem;
- testar firmware;
- confirmar estabilidade.

### Perfboard ponto-a-ponto

Usar apenas quando o circuito estiver validado.

Cada pad/furo é tratado como um ponto independente; as ligações são criadas com soldadura, pernas dos componentes e/ou fios/jumpers.

```text
breadboard
   |
   v
protótipo validado
   |
   v
perfboard
   |
   v
soldadura
   |
   v
instalação na carrinha
```

## Protótipo validado — COMCS PL6

- ESP32-S3 com DHT11 da aula publica por MQTT/TLS (porta 8883).
- Tópicos: `comcs/pl6/temperature`, `comcs/pl6/humidity`, `comcs/pl6/heatindex`.
- Node-RED 5 com FlowFuse Dashboard 2 no Ubuntu recebe as mensagens do EMQX Cloud.
- Dashboard com indicadores de temperatura e humidade, consultado também no telemóvel.
- Leituras observadas: 22,6 °C e 48% (exemplo pontual, não histórico).
- Para a carrinha, criar tópicos próprios: `van/h100/temperature`, `van/h100/humidity`, `van/h100/status`.

## Próximo passo — bancada

Não soldar ainda.

Montar apenas:

```text
ESP32 + 1 DHT22
```

Objetivo do primeiro teste:

```text
Temperature: xx.x C
Humidity:    xx.x %
```

Depois da leitura estável:

1. confirmar pinagem definitiva;
2. confirmar alimentação USB da carrinha com multímetro;
3. preparar disposição física na caixa;
4. migrar para perfboard;
5. soldar bornes removíveis;
6. adicionar OLED numa fase seguinte.

Não é necessário comprar outra breadboard antes deste teste.

## Expansões futuras

Depois da V1 ambiental estar estável:

- OLED local;
- leitura da tensão da bateria auxiliar;
- leitura da tensão da bateria de arranque;
- temperatura exterior;
- estado/consumo do frigorífico;
- histórico no Raspberry Pi;
- alarmes de temperatura, humidade e bateria;
- MQTT/TLS + Node-RED;
- integração com Tailscale para acesso remoto ao dashboard.

## Segurança e limitações

- Nunca guardar passwords, `secrets.h`, tokens ou certificados privados no Git.
- Validar certificado TLS do broker e configurar autenticação/ACL MQTT.
- Não expor a interface de administração do Node-RED à Internet pública; proteger o editor e usar Tailscale.
- Sem hotspot ativo, o ESP32 não transmite e o dashboard não recebe novas medições. O Raspberry Pi pode continuar a servir o dashboard, mas precisa de guardar histórico para mostrar dados anteriores.
- Não alimentar diretamente o ESP32 a partir dos 12–14 V da carrinha.
- Confirmar a tensão real da saída USB antes da instalação.
- Desligar a alimentação antes de alterar cablagem.
- Só passar da breadboard para soldadura depois de o circuito estar validado.

## Tracking

Issue: #11 — H100 monitor: registar hardware recebido e preparar protótipo ESP32 + DHT22.
