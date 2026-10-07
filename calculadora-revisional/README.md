# Calculadora Revisional

Página única (`index.html`, sem dependências além das fontes do Google Fonts) que reconstrói a dívida de um contrato bancário com base apenas nas condições contratuais. É o primeiro passo do parecer técnico contábil; a comparação com a taxa média do BACEN e a apuração do indébito ficam para a etapa seguinte.

Para usar, abra `index.html` no navegador. Os dados digitados ficam salvos só no navegador (`localStorage`).

## Entrada

Os campos marcados com asterisco vermelho são obrigatórios.

| Campo | Observação |
|---|---|
| Sistema de amortização | Price ou SAC |
| Valor a calcular | Só na Price. Informe três entre parcela, taxa, prazo e valor financiado; a calculadora encontra o quarto |
| Data do contrato e 1º vencimento | O 1º período usa os dias efetivos entre as datas (base 30) |
| Seguro e tarifas financiados | Opcionais; entram no CET e geram alertas |
| Capitalização de juros | Caixa de seleção: define juros compostos ou simples nos encargos do atraso |
| Encargos do atraso | Juros remuneratórios, mora e multa, ou comissão de permanência |
| Feriados locais | Fins de semana e feriados bancários nacionais já são considerados |
| Pagamentos | Data e valor; aceita colar duas colunas do Excel |
| Apuração do saldo devedor | Data opcional para apurar o saldo |

## Critérios de cálculo

- **Pagamento de parcela vencida:** padrão pela imputação do art. 354 do Código Civil (encargos primeiro, depois capital). A opção proporcional divide o valor entre encargos e capital.
- **Encargos do atraso:** multa cobrada uma vez sobre o principal em aberto; juros de mora simples, pro rata; juros remuneratórios compostos ou simples conforme a capitalização.
- **Comissão de permanência:** substitui os demais encargos (Súmula 472/STJ). A calculadora alerta quando a taxa supera a soma dos juros remuneratórios e de mora do contrato.
- **Dia útil:** pagamento no dia útil seguinte a fim de semana ou feriado bancário não gera encargos.
- **Valor pago além das parcelas vencidas:** antecipa parcelas futuras com desconto à taxa do contrato (art. 52, § 2º, CDC; Res. CMN 3.516/2007), reduzindo o prazo ou o valor da parcela.
- **CET:** calculado sobre o valor liberado (financiado menos seguro e tarifas). Não inclui IOF.
- **Saldo devedor:** parcelas a vencer pelo valor presente e pelo valor nominal, mais parcelas vencidas e encargos.

## Diferença em relação à Calculadora do Cidadão

A Calculadora do Cidadão (Banco Central) considera o 1º vencimento 30 dias após o contrato. Quando o 1º período é maior ou menor, os valores calculados divergem, e a aba "Premissas do cálculo" registra isso.

## Alertas

Cada alerta traz o indício ou o fundamento normativo e uma lista do que averiguar no contrato e nos extratos:

| Alerta | Fundamento |
|---|---|
| Multa acima de 2% | Art. 52, § 1º, CDC; art. 9º do Decreto 22.626/1933 |
| Juros de mora acima de 1% a.m. | Súmula 379/STJ |
| Comissão de permanência acima do teto | Súmulas 30, 294 e 472/STJ; REsp 1.058.114/RS |
| Price sem capitalização pactuada | Súmulas 539 e 541/STJ; MP 2.170-36/2001 |
| Parcelas vencidas em aberto | Art. 397 do Código Civil; REsp 1.061.530/RS |
| Seguro financiado | Art. 39, I, CDC; Tema 972/STJ |
| Tarifas financiadas | Res. CMN 3.919/2010; Temas 618 a 620 e 958/STJ |
| Pagamento acima do saldo | Art. 876 do Código Civil; art. 42, parágrafo único, CDC |
| Amortização extraordinária | Art. 52, § 2º, CDC; Res. CMN 3.516/2007 |
| CET acima da taxa de juros | Res. CMN 4.881/2020 |

## Saída

Abas: Resumo, Tabela de amortização, Situação das parcelas, Pagamentos, Premissas do cálculo e Relatório. O relatório pode ser copiado em formato compatível com o Word.
