# Registo de inspeção elétrica — 2026-10-27

**Veículo:** Hyundai H100 FD 27XP, 1994, gasóleo, 2476 cm³. Ver [veiculo.md](./veiculo.md) e [guia de fusíveis e relés](./h100-1994-fusiveis-reles.md).

## Observações e medições reportadas pelo proprietário

| Campo | Observação | Estado da evidência |
| --- | --- | --- |
| Data | 27 de outubro de 2026 | Confirmado pelo proprietário |
| Local da fotografia | Compartimento da bateria / acesso sob a carroçaria | Observável na fotografia partilhada na conversa |
| Bateria | Bateria automóvel instalada, com cabos e terminais visíveis | Fotografia partilhada na conversa; não incorporada ainda no Git |
| Tensão com motor a trabalhar | **14,0 V** | Reportada verbalmente; condições/instrumento não registados |
| Tensão com motor desligado | **13,5 V** | Valor corrigido explicitamente pelo proprietário |
| Ventilador da sofagem | Funcionamento anteriormente intermitente; deixou de funcionar | Sintoma reportado |
| Limpa-vidros direito | Não funciona | Sintoma reportado; sem confirmação do estado do esquerdo nesta inspeção |

## Interpretação técnica preliminar

- **14,0 V com o motor ligado** é compatível com funcionamento do sistema de carga, embora uma medição isolada não permita testar integralmente o alternador.
- **13,5 V com o motor desligado** foi o valor corrigido pelo proprietário. Pode ocorrer pouco depois de desligar o motor por carga superficial; para avaliação da bateria é útil medir novamente depois de um período de repouso.
- A leitura inicial de 3,5 V resultou de uma transcrição incorreta e foi substituída por **13,5 V** após correção explícita em 27-10-2026.
- Não concluir que os defeitos do ventilador e do limpa-vidros têm a mesma causa. Se apenas um braço de limpa-vidros não funcionar, investigar também acoplamento mecânico e ligação das hastes.

## Próximo teste (não realizado)

1. Motor desligado, ignição desligada, multímetro em **V DC**, medir diretamente **poste positivo → poste negativo** da bateria e registar a tensão.
2. Repetir **terminal positivo → terminal negativo** (pinças/cabos) e comparar, sem curto-circuitar com as pontas de prova.
3. Registar instrumento, escala e se houve tempo de repouso após desligar o motor.
4. Fotografar a etiqueta completa da bateria, os terminais e o visor durante a medição; não divulgar identificadores pessoais.
5. Só depois avançar para os circuitos BLOWER/HEATER e WIPER conforme identificação física.

**Fotografia:** recebida na conversa de 27-10-2026 (bateria vista no respetivo compartimento). Ainda **não adicionada como ficheiro binário ao GitHub**; preservar separadamente para futura inclusão em `Fotos/`.

## Teste de fusível — 27-10-2026

- **Componente:** fusível automóvel azul, **15 A**, retirado da caixa de fusíveis do habitáculo.
- **Instrumento:** UNI-T UT125C em modo continuidade; teste realizado com fusível retirado e ignição desligada.
- **Controlo do equipamento:** as duas pontas encostadas entre si produzem sinal sonoro (continuidade confirmada).
- **Medição do fusível:** pontas nas duas pernas metálicas; visor **OL**, sem sinal sonoro no fusível segundo a sequência de testes fotografada.
- **Resultado:** **fusível de 15 A fundido / sem continuidade**, de acordo com a leitura apresentada.
- **Circuito / posição física exata:** ainda não identificados pela legenda; não atribuir ao limpa-vidros nem à sofagem sem confirmação.
- **Ação pendente:** identificar posição e circuito e verificar possível causa antes de instalar um fusível novo do mesmo tipo e amperagem especificada.
- **Evidência fotográfica:** partilhada na conversa de 27-10-2026; ainda não incorporada no GitHub.

> Segurança: não fazer pontes, não aumentar a amperagem e não realizar teste de continuidade em circuito alimentado.

> Este registo transcreve as observações efetuadas, sem inventar medições nem diagnosticar avarias que ainda não foram isoladas.

## Teste sistemático — fila inferior da caixa de fusíveis (27-10-2026)

Resultados comunicados pelo proprietário, com fusíveis retirados individualmente e multímetro UNI-T UT125C no modo de continuidade. Identificadores #1–#8 são **ordem de inspeção da esquerda para a direita**, não números oficiais dos circuitos.

| Ordem no teste | Fusível identificado | Leitura | Estado |
| --- | --- | --- | --- |
| #1 | Azul, 15 A (primeiro ocupado à esquerda) | OL, sem apito | **Fundido** |
| #2 | Vermelho, 10 A | Apita | Continuidade OK |
| #3 | Amarelo, 20 A | Apita | Continuidade OK |
| #4 | Amarelo, 20 A | Apita | Continuidade OK |
| #5 | Vermelho, 10 A | Apita | Continuidade OK |
| #6 | Azul, 15 A | Apita | Continuidade OK |
| #7 | Azul, 15 A | Apita | Continuidade OK |
| #8 | Extremo direito, amperagem/posição a confirmar | Apita | Continuidade OK |

**Balanço:** 7 com continuidade, 1 sem continuidade. Ainda não está estabelecida a correspondência entre estas posições e os circuitos WIPER/HEATER. A continuidade dos fusíveis não comprova que a alimentação chega aos equipamentos. Evitar substituir ou energizar o circuito do fusível fundido sem confirmar legenda e valor nominal.

**Próxima verificação:** identificar o circuito do fusível #1 através da legenda/tampa e testar a fila superior com o mesmo procedimento (ignição desligada, um fusível de cada vez), mantendo os resultados separados.
