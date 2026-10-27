# Registo de inspeção elétrica — 2026-10-27

**Veículo:** Hyundai H100 FD 27XP, 1994, gasóleo, 2476 cm³. Ver [veiculo.md](./veiculo.md) e [guia de fusíveis e relés](./h100-1994-fusiveis-reles.md).

## Observações e medições reportadas pelo proprietário

| Campo | Observação | Estado da evidência |
| --- | --- | --- |
| Data | 27 de outubro de 2026 | Confirmado pelo proprietário |
| Local da fotografia | Compartimento da bateria / acesso sob a carroçaria | Observável na fotografia partilhada na conversa |
| Bateria | Bateria automóvel instalada, com cabos e terminais visíveis | Fotografia partilhada na conversa; não incorporada ainda no Git |
| Tensão com motor a trabalhar | **14,0 V** | Reportada verbalmente; condições/instrumento não registados |
| Tensão com motor desligado | **3,5 V** | Reportada verbalmente; **valor crítico a reconfirmar** |
| Ventilador da sofagem | Funcionamento anteriormente intermitente; deixou de funcionar | Sintoma reportado |
| Limpa-vidros direito | Não funciona | Sintoma reportado; sem confirmação do estado do esquerdo nesta inspeção |

## Interpretação técnica preliminar

- **14,0 V com o motor ligado** é compatível com tensão de carga normal do alternador, mas uma única medição não valida todo o sistema de carga.
- **3,5 V com motor desligado** é extraordinariamente baixo para uma bateria chumbo-ácido de 12 V e não é compatível com uma bateria normalmente operacional. Antes de atribuir falha à bateria, confirmar **se o valor foi mesmo 3,5 V (e não 13,5 V)**, em que escala e em que pontos do circuito foi feita a medição.
- Se for **3,5 V medidos diretamente entre os dois postes da bateria com motor desligado**, tratar como possível falha grave da bateria/medição e procurar avaliação adequada antes de depender do veículo. Se a medida for nos terminais/cabos e não nos postes, verificar também contactos e massa.
- Não concluir que os defeitos do ventilador e do limpa-vidros têm a mesma causa. Se apenas um braço de limpa-vidros não funcionar, investigar também acoplamento mecânico e ligação das hastes.

## Próximo teste (não realizado)

1. Motor desligado, ignição desligada, multímetro em **V DC**, medir diretamente **poste positivo → poste negativo** da bateria e registar a tensão.
2. Repetir **terminal positivo → terminal negativo** (pinças/cabos) e comparar, sem curto-circuitar com as pontas de prova.
3. Registar instrumento, escala e se houve tempo de repouso após desligar o motor.
4. Fotografar a etiqueta completa da bateria, os terminais e o visor durante a medição; não divulgar identificadores pessoais.
5. Só depois avançar para os circuitos BLOWER/HEATER e WIPER conforme identificação física.

**Fotografia:** recebida na conversa de 27-10-2026 (bateria vista no respetivo compartimento). Ainda **não adicionada como ficheiro binário ao GitHub**; preservar separadamente para futura inclusão em `Fotos/`.

> Este registo transcreve as observações efetuadas, sem inventar medições nem diagnosticar avarias que ainda não foram isoladas.
