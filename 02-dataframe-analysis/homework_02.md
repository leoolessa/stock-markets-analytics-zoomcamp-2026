# Homework 2 — One Dataframe (cohort 2026)

Objetivo geral: combinar dados de fontes variadas (IPOs, preços de ações) no Pandas e gerar features adicionais.

- Prazo: **28 de setembro de 2026, 22:59** — confirmado na [página oficial do curso](https://courses.datatalks.club/sma-zoomcamp-2026/) (atenção: o `README.md` do módulo ainda está com a data antiga de 16/09, o prazo foi empurrado — conferir sempre na página oficial antes de submeter)
- Enunciado oficial: https://github.com/DataTalksClub/stock-markets-analytics-zoomcamp/blob/main/cohorts/2026/homework2.md
- Submissão: https://courses.datatalks.club/sma-zoomcamp-2026/homework/hw02
- Leaderboard: https://courses.datatalks.club/sma-zoomcamp-2026/leaderboard

---

## Questão 1 — [IPO] Withdrawn IPOs by Company Type

**Pergunta principal**: Qual é o valor total de IPOs retirados (em $ milhões) para a classe de empresa com maior valor total de retirada?

- [ ] Carregar a tabela "Recently Filed" do iposcoop.com (https://www.iposcoop.com/ipos-recently-filed/) com `pandas.read_html()`
- [ ] Filtrar apenas as linhas onde `Expected To Trade` é `Withdrawn` (esperado: 32 entradas)
- [ ] Criar a coluna `Company Type`, classificando o nome da empresa por padrões, **NA ORDEM abaixo** (a primeira regra que bater vence):
  - "Technologies" -> Technologies
  - "Acquisition Corp" / "Acquisition Corporation" / "Corp" -> Acquisition Corp
  - "Inc" / "Incorporated" -> Inc.
  - "Group" -> Group
  - "Ltd" / "Limited" -> Limited
  - "Holdings" / "Holding" -> Holdings
  - Outros -> Other
- [ ] Criar a coluna `Avg_price`: parsear `Price Low` e `Price High` (ex: `$8.00` -> `8.0`) e tirar a média; tratar `-`/vazio como `None`/`NaN`
- [ ] Converter `Shares (millions)` e `Est $ Vol (millions)` para numérico, limpando `$` e `,`
- [ ] Criar a coluna `Shares_offered_value`: se `Shares (millions) * Avg_price` não for nulo, usar esse valor; senão usar `Est $ Vol (millions)`
- [ ] Agrupar por `Company Type` e somar `Shares_offered_value`

**Resposta:** _(preencher)_

---

## Questão 2 — [IPO] Median Sharpe Ratio for 2025 IPOs (First 8 Months)

**Pergunta principal**: Qual é o índice de Sharpe mediano (em 11/09/2026) para empresas que abriram capital antes de 01/09/2025?

- [ ] Baixar a lista de 231 IPOs de 2025 em https://www.iposcoop.com/2025-pricings/
- [ ] Filtrar `Offer Date` antes de 01/09/2025 e excluir retorno 0% (esperado: 148 ações)
- [ ] Baixar dados diários via `yfinance` para `stocks_df`, tratando tickers ausentes/deslistados (esperado: ~134 ações)
- [ ] Calcular `growth_252d = Close / Close.shift(252)`
- [ ] Calcular volatilidade anualizada: `stocks_df['volatility'] = stocks_df['Close'].rolling(30).std() * np.sqrt(252)`
- [ ] Calcular Sharpe com taxa livre de risco de 5%: `stocks_df['Sharpe'] = (stocks_df['growth_252d'] - 0.05) / stocks_df['volatility']`
- [ ] Filtrar apenas o dia `2026-09-11` e rodar `.describe()`

**Observações sugeridas**: comparar mediana vs. média do `growth_252d` (outliers de alto crescimento distorcem a média?); ver quantas ações chegaram nos 252 dias de negociação.

**Resposta:** _(preencher)_

---

## Questão 3 — [IPO] 'Fixed Months Holding Strategy'

**Pergunta principal**: Qual é o número ideal de meses (1 a 12) para segurar uma ação recém-IPO'd, maximizando o crescimento mediano?

- [ ] Usar o `stocks_df` já filtrado na Questão 2
- [ ] Calcular 12 colunas de crescimento futuro: `future_growth_1_m` ... `future_growth_12_m` (1 mês = 21 dias úteis, até 12 meses = 252 dias)
- [ ] Para cada ticker, achar o primeiro dia de negociação (`min_date`) e seu preço de fechamento
- [ ] Fazer inner join entre os registros de `min_date` e o dataset completo de crescimento
- [ ] Rodar `.describe()` nas 12 colunas e identificar em qual mês a mediana (percentil 50) é maior

**Resposta:** _(preencher)_

---

## Questão 4 — [Strategy] Simple RSI-Based Trading Strategy

**Pergunta principal**: Qual seria o lucro total (em $ mil) investindo $1.000 toda vez que uma ação estivesse sobrevendida (RSI < 30)?

- [ ] Baixar o parquet fornecido via `gdown` (file_id: `1grCTCzMZKY5sJRtdbLVCXg8JXA8VPyg-`) e ler com `pd.read_parquet(..., engine="pyarrow")`
- [ ] Definir sinal de sobrevenda: RSI < 30
- [ ] Filtrar sinais entre `2000-01-01` e `2025-06-01`
- [ ] Calcular lucro: `net_income = 1000 * (selected_df['growth_future_30d'] - 1).sum()`

**Resposta:** _(preencher)_

---

## Questão 5 — [Exploratory, Optional] Predicting a Positive-Return IPO

**Pergunta**: Como você mudaria a estratégia pra aumentar a lucratividade em IPOs, já que a maioria das abordagens tradicionais dá retorno negativo (média, mediana e até percentil 75)?

- [ ] Brainstorm de ideias e escrever a resposta (pergunta aberta, não tem gabarito)

**Resposta:** _(preencher)_
