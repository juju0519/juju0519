# Calculadora Revisional

Página única (`index.html`, sem dependências além das fontes do Google Fonts) que faz a Reconstrução da dívida de um contrato bancário com base apenas nas condições contratuais. É o primeiro passo do parecer técnico contábil; a comparação com a taxa média do BACEN e a apuração do indébito ficam para a etapa seguinte.

Para usar, abra `index.html` no navegador. Os dados digitados ficam salvos só no navegador (`localStorage`).

## Termos definidos

A calculadora usa os termos definidos do glossário do escritório, com inicial maiúscula: Valor Financiado, Valor Liberado, Valor da Parcela, Soma das Prestações, Parcela Vincenda, Parcela em Atraso, Encargos de Atraso, Pagamento Extraordinário, Valor Total Pago, Capital Pago, Data-Base, Saldo Devedor Reconstruído e Reconstrução.

## Entrada

Os campos com asterisco vermelho ao lado do nome são obrigatórios.

| Campo | Observação |
|---|---|
| Sistema de amortização | Price ou SAC |
| Valor Financiado, nº de parcelas, taxa e Valor da Parcela | Na Price, informe três; o campo deixado em branco é calculado. Com os quatro informados, o cronograma usa o Valor da Parcela informado. No SAC, a parcela é sempre calculada |
| Data de celebração e 1º vencimento | O 1º período usa os dias efetivos entre as datas |
| Seguro e tarifas financiados | Opcionais; entram no CET e geram alertas |
| Capitalização de juros | Caixa de seleção. Marcada, abre a periodicidade: mensal ou diária |
| Comissão de permanência | Opcional. Preenchida, desativa multa, juros de mora e juros remuneratórios do atraso |
| Feriados locais | Fins de semana e feriados bancários nacionais já são considerados |
| Pagamentos | Data e valor; aceita colar duas colunas do Excel |
| Data-Base | Opcional; apura o Saldo Devedor Reconstruído nessa data |

## Critérios de cálculo

- **Capitalização mensal:** juros de normalidade com mês de 30 dias e fator (1 + i)^(dias ÷ 30) no 1º período; encargos remuneratórios do atraso em juros compostos.
- **Capitalização diária:** taxa diária igual à taxa mensal ÷ 30, capitalizada por dia corrido, na fase de normalidade e no atraso. O Valor da Parcela, a taxa, o prazo ou o Valor Financiado calculados seguem a mesma regra. A taxa efetiva mensal e anual resultante aparece no resumo.
- **Sem capitalização:** encargos remuneratórios do atraso em juros simples.
- **Pagamento de Parcela em Atraso:** padrão pela imputação do art. 354 do Código Civil (encargos primeiro, depois capital). A opção proporcional divide o valor entre encargos e capital.
- **Encargos de Atraso:** multa cobrada uma vez sobre o principal em aberto; juros de mora simples, pro rata; juros remuneratórios conforme a capitalização.
- **Comissão de permanência:** substitui os demais Encargos de Atraso (Súmula 472/STJ). O teto de comparação é a taxa de juros do contrato mais 1% a.m. de mora (REsp 1.058.114/RS).
- **Dia útil:** pagamento no dia útil seguinte a fim de semana ou feriado bancário não gera encargos.
- **Pagamento Extraordinário:** valor pago além das Parcelas em Atraso antecipa Parcelas Vincendas com desconto à taxa do contrato (art. 52, § 2º, CDC; Res. CMN 3.516/2007), reduzindo o prazo ou o Valor da Parcela.
- **CET:** calculado sobre o Valor Liberado (Valor Financiado menos seguro e tarifas). Não inclui IOF.
- **Saldo Devedor Reconstruído:** Parcelas em Atraso com Encargos de Atraso até a Data-Base, mais Parcelas Vincendas pelo valor presente e pelo valor nominal.

## Diferença em relação à Calculadora do Cidadão

A Calculadora do Cidadão (Banco Central) considera o 1º vencimento 30 dias após o contrato e capitalização mensal. Quando o 1º período é maior ou menor, ou a capitalização é diária, os valores calculados divergem, e a aba "Premissas do cálculo" registra isso.

## Alertas

Cada alerta traz o indício ou o fundamento normativo e uma lista do que averiguar no contrato e nos extratos:

| Alerta | Fundamento |
|---|---|
| Multa acima de 2% | Art. 52, § 1º, CDC; art. 9º do Decreto 22.626/1933 |
| Juros de mora acima de 1% a.m. | Súmula 379/STJ |
| Comissão de permanência acima do teto | Súmulas 30, 294 e 472/STJ; REsp 1.058.114/RS |
| Capitalização diária | REsp 1.826.463 (STJ, 3ª Turma, 2020); arts. 6º, III, e 46 do CDC |
| Price sem capitalização pactuada | Súmulas 539 e 541/STJ; MP 2.170-36/2001 |
| Parcelas em Atraso | Art. 397 do Código Civil; REsp 1.061.530/RS |
| Seguro financiado | Art. 39, I, CDC; Tema 972/STJ |
| Tarifas financiadas | Res. CMN 3.919/2010; Temas 618 a 620 e 958/STJ |
| Pagamento acima do saldo | Art. 876 do Código Civil; art. 42, parágrafo único, CDC |
| Pagamento Extraordinário | Art. 52, § 2º, CDC; Res. CMN 3.516/2007 |
| CET acima da taxa de juros | Res. CMN 4.881/2020 |

## Saída

Abas: Resumo, Tabela de amortização, Situação das parcelas, Pagamentos, Premissas do cálculo e Relatório. O relatório pode ser copiado em formato compatível com o Word.
