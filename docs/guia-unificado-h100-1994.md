# Hyundai H100 1994 — guia unificado de fusíveis e manutenção

**Van of Freedom — versão 01-11-2026**  
**PDF correspondente (a arquivar):** `docs/manuais/H100_1994_Guia_Unificado_Fusiveis.pdf`  
**Nota:** o PDF foi gerado a partir das fotografias e registos da conversa. A cópia binária deve ser adicionada ao repositório; este ficheiro Markdown é o índice consolidado disponível no GitHub.

## Orientação fundamental

A carrinha tem uma caixa no habitáculo com **fila superior** e **fila inferior**. Nas tabelas, `#1`, `#2` etc. são a **ordem dos testes feitos da esquerda para a direita, NÃO a numeração oficial dos circuitos Hyundai**. Como a legenda original não está identificada, **não podemos atribuir WIPER, HEATER/BLOWER, CIGAR etc. a uma posição específica**.

Fotografia original da caixa: incluída no PDF. A fotografia permite visualizar as filas, mas não confirma a aplicação de cada posição.

## Fila inferior — oito testes reportados

| Ordem dos testes | Identificação na conversa | Continuidade UNI-T UT125C |
| --- | --- | --- |
| #1 | Azul 15 A | **OL / não apitou** |
| #2 | Vermelho 10 A | Apitou |
| #3 | Amarelo 20 A | Apitou |
| #4 | Amarelo 20 A | Apitou |
| #5 | Vermelho 10 A | Apitou |
| #6 | Azul 15 A | Apitou |
| #7 | Azul 15 A | Apitou |
| #8 | Extremo direito — valor a confirmar | Apitou |

## Fila superior — testes efetivamente comunicados

| Ordem dos testes | Identificação | Continuidade |
| --- | --- | --- |
| #1 | Não especificada | Apitou |
| #2 | Azul 15 A | **OL / não apitou** |
| Restantes | Não temos o registo sistemático completo | Desconhecido |

**Resumo:** dois testes `OL` em fusíveis azuis 15 A, e oito medições que apitaram. Os resultados `OL` foram comunicados com multímetro em modo continuidade e pontas em contacto. O proprietário referiu ter substituído fusíveis em 01-11-2026; isso **não resolveu de modo sustentado a sofagem**. Este registo preserva as leituras, sem inventar a função de cada fusível.

### Procedimento aplicado

1. Ignição desligada; retirar **um fusível de cada vez**.
2. UNI-T UT125C em continuidade, ponta preta em COM e vermelha em V/Ω; pontas juntas apitam.
3. Medir entre as duas pernas do fusível retirado.
4. Apita = continuidade; `OL` = circuito aberto na medição, verificar contacto antes de diagnosticar definitivamente.
5. Repor no **mesmo encaixe**, com amperagem e formato especificados. Não preencher espaços vazios ao acaso, não fazer pontes e não usar amperagem superior.

## Avarias atuais — próximas verificações

| Sistema | Sintoma | Issue |
| --- | --- | --- |
| Ventilador da sofagem | Ligou durante segundos e parou; não sopra ar em nenhuma velocidade. Investigar ficha, tensão, massa, motor/interruptor | [#3](https://github.com/abaltazapinto/OFF-GRID/issues/3) |
| Limpa-vidros direito | Braço roda em sentido/posição errados; esquerdo funciona; verificar fixação e transmissão sem acionar desalinhado | [#4](https://github.com/abaltazapinto/OFF-GRID/issues/4) |
| Esguicho esquerdo | Não pulveriza bem; base exterior húmida. Bico é **exterior, na peça preta sob o para-brisas**. Limpar suavemente e observar escorrimento; não começar por desmontar tablier | [#5](https://github.com/abaltazapinto/OFF-GRID/issues/5) |
| Tomada 12 V / isqueiro | A luz funciona mas não alimenta acessórios; verificar tensão no centro e massa lateral | [#6](https://github.com/abaltazapinto/OFF-GRID/issues/6) |
| Caixa de fusíveis | Posições vazias sem função identificada e histórico de amarelo 20 A solto. Precisamos da legenda da versão exata | [#7](https://github.com/abaltazapinto/OFF-GRID/issues/7) |

## Identificação e alimentação

- Hyundai H100 FD 27XP, 1ª matrícula 19-12-1994, gasóleo, 2476 cm³, 55 kW.
- Bateria: 14,0 V reportados a trabalhar; 13,5 V reportados desligada.
- Não afirmar que lugares vazios precisam ser preenchidos.
- Confirmar amperagem prescrita pela legenda/manual aplicável ao chassis.

## Reparações e custos 2026

| Item | Valor |
| --- | ---: |
| Kit camper + acessórios, fatura no repositório | 2.390 € |
| Canhão da fechadura | 95 € |
| Chave suplente | 5 € |
| Rodo Pereira — alternador, bateria, radiador, mangueiras e líquido de refrigeração (fatura na aldeia) | 1.026 € |
| **Total registado** | **3.516 €** |

Não inclui custo de fusíveis Norauto sem preço de compra comprovado.

## Referências externas

- https://www.autogenius.info/hyndai-h100-1986-1996-fuse-box-diagram/
- https://carmanualshub.com/hyundai-h100-1995-fuses-block-and-relays/
- https://fuseandrelay.com/hyundai/grace-h100.html
- [Índice de catálogos e manuais](./documentacao-tecnica-h100-1994.md).
- [Inspeção elétrica original](./inspecao-eletrica-2026-10-27.md).
- [Histórico de compras](../Compras/remodelacao-2026.md).

**Aplicabilidade:** estas referências podem abranger mercados e versões diferentes. O PDF unificado e este Markdown são um **registo de campo**, não um manual de oficina original homologado para o VIN.
