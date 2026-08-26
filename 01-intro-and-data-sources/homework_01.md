# Homework 1 — Data Sources (cohort 2026)

Objetivo geral: baixar dados financeiros de fontes variadas e fazer cálculos/análises simples.

- Prazo: **2026-09-02**
- Enunciado oficial: https://github.com/DataTalksClub/stock-markets-analytics-zoomcamp/blob/main/cohorts/2026/homework1.md
- Submissão: https://courses.datatalks.club/sma-zoomcamp-2026/homework/hw01
- Leaderboard: https://courses.datatalks.club/sma-zoomcamp-2026/leaderboard

---

## Questão 1 — S&P 500 Stocks Added to the Index

**Pergunta principal**: Which year had the highest number of additions (starting from 2020)?

- [ ] Usar a página da Wikipédia com as empresas do S&P 500 e baixar com `pandas.read_html()`
- [ ] Incluir headers HTTP (`'User-Agent': 'Mozilla/5.0...'`) na requisição
- [ ] Criar um DataFrame com tickers, nomes e ano de adição
- [ ] Extrair o ano a partir da data de adição
- [ ] Calcular o número de ações adicionadas por ano
- [ ] Identificar o ano com maior número de adições desde 2020

**Pergunta adicional**: Quantas ações atuais do S&P 500 estão no índice há mais de 20 anos?
- [ ] Calcular essa contagem

**Resposta:** _(preencher)_

---

## Questão 2 — Indexes YTD (as of 21 August 2026)

**Pergunta principal**: How many indexes (out of 10) have better year-to-date returns than the US (S&P 500) as of August 21, 2026?

- [ ] Buscar no Yahoo Finance os 10 índices globais: S&P 500 (`^GSPC`), Shanghai Composite (`000001.SS`), HANG SENG (`^HSI`), S&P/ASX 200 (`^AXJO`), Nifty 50 (`^NSEI`), S&P/TSX (`^GSPTSE`), DAX (`^GDAXI`), FTSE 100 (`^FTSE`), Nikkei 225 (`^N225`), IPC Mexico (`^MXX`), Ibovespa (`^BVSP`)
- [ ] Baixar com `yfinance`, `start_date='2026-01-01'`, `end_date='2026-08-21'`
- [ ] Calcular o crescimento YTD usando os preços de fechamento
- [ ] Contar quantos índices superaram o S&P 500 no período

**Pergunta adicional**: Quantos desses índices têm retornos melhores que o S&P 500 em 3, 5 e 10 anos? Existe a mesma tendência?
- [ ] Calcular e comparar

**Resposta:** _(preencher)_

---

## Questão 3 — S&P 500 Market Corrections Analysis

**Pergunta principal**: Calculate the median drawdown (in %) of significant market corrections in the S&P 500 index.

> Correção = queda de pelo menos 5% em relação ao máximo histórico mais recente.

- [ ] Baixar dados históricos diários do S&P 500 com `yfinance` (1950 até hoje)
- [ ] Identificar todos os pontos de máxima histórica (preço maior que todos os dias anteriores)
- [ ] Para cada par consecutivo de máximas, encontrar o preço mínimo entre elas
- [ ] Calcular o drawdown: `(high - low) / high * 100`
- [ ] Filtrar correções com drawdown ≥ 5%
- [ ] Calcular a duração (em dias) de cada correção
- [ ] Determinar os percentis 25º, 50º (mediana) e 75º de duração e de drawdown

**Resposta:** _(preencher)_

---

## Questão 4 — Earnings Surprise Analysis for Amazon (AMZN)

**Pergunta principal**: Calculate the median 2-day percentage change in stock prices following positive earnings surprise days.

- [ ] Carregar dados de earnings com `yf.Ticker('AMZN').get_earnings_dates()` (25 entradas desde 2020-10-29)
- [ ] Baixar o histórico completo de preços com `yfinance`
- [ ] Calcular o retorno de 2 dias: `Close_Day3 / Close_Day1 - 1` (sequências de 3 dias úteis consecutivos)
- [ ] Filtrar apenas os dias de surpresa positiva de earnings
- [ ] Calcular a mediana do retorno de 2 dias
- [ ] Calcular a correlação entre o retorno de 2 dias e a magnitude da surpresa (`pd.corr()`)

**Pergunta adicional**: Há correlação entre a magnitude da surpresa e a reação do preço? O mercado reage diferente em bull vs bear markets?
- [ ] Analisar e responder

**Resposta:** _(preencher)_

---

## Questão 5 — Brainstorm Capstone Project (opcional)

**Pergunta**: Describe the capstone project you would like to pursue, considering aspirations, ML model predictions, and prior knowledge.

- [ ] Definir classe de ativo, país, vertical industrial ou estratégia de investimento
- [ ] Escrever a ideia do projeto final

**Resposta:** _(preencher)_

---

## Questão 6 — Investigate New Metrics (opcional)

**Pergunta**: Download and explore additional metrics or time series valuable for your project.

- [ ] Escolher métricas/séries adicionais relevantes para o seu projeto
- [ ] Explicar por que cada métrica é útil
- [ ] Explicar como recuperá-la via Python
- [ ] Identificar as fontes de dados

**Resposta:** _(preencher)_
