# Teste A/B simulado — método completo de experimentação

Projeto de portfólio de **Marketing Data Science**: o ciclo completo de um teste A/B feito com método,
aplicado a um caso real de tráfego pago — decidir se uma **nova landing page** converte mais leads em
compradores que a página atual.

> Demonstra o que separa testar com rigor de testar no improviso: **planejar a amostra antes,
> simular o experimento, analisar com intervalo de confiança + teste de hipótese, corrigir múltiplas
> métricas e fechar com um relatório executivo de decisão.**

> **English summary.** End-to-end A/B test on a landing page: sample size planned before the test
> (80% power, 95% confidence), simulated experiment, Wilson confidence intervals, two-proportion z-test,
> Bayesian P(B>A), Bonferroni and Benjamini-Hochberg corrections on secondary metrics, and an executive
> decision report. Notebook written in Portuguese; data is synthetic and reproducible.

## Resultado em uma linha

B converteu **11,8%** contra **10,0%** de A (diferença de +1,8 p.p., IC 95% de +0,4 a +3,2, p = 0,0105,
P(B>A) = 99,5%). Duas métricas secundárias que "pareciam" significativas (CTR e taxa de rejeição) não
resistiram à correção para múltiplos testes: eram falsos positivos.

## O que o projeto mostra

| Etapa | Conteúdo |
|---|---|
| **1. Planejamento** | Cálculo de tamanho de amostra e duração *antes* do teste (poder 80%, confiança 95%) |
| **2. Simulação** | Geração de dados sintéticos realistas com um efeito real plantado em B |
| **3. Análise primária** | Taxa de conversão, **IC de Wilson**, teste z de duas proporções, **P(B>A)** bayesiana |
| **4. Múltiplos testes** | Métrica primária julgada sozinha; correção **Bonferroni** e **Benjamini-Hochberg** nas secundárias → falsos positivos identificados |
| **5. Relatório executivo** | Recomendação de decisão clara, no formato que um cliente/diretoria lê |

## Notebook

[`projeto-ab-test-landing.ipynb`](projeto-ab-test-landing.ipynb)

## Stack

Python 3.11+ via [`uv`](https://docs.astral.sh/uv/) · `numpy`, `pandas`, `scipy`, `matplotlib`, `jupyterlab`.

## Como rodar

```bash
uv sync
uv run jupyter lab    # ou abra o .ipynb no VS Code e selecione o kernel do .venv
```

## Principais conclusões metodológicas

- **Dimensione antes:** efeitos pequenos exigem muita amostra; decidir sem amostra mínima é decidir no ruído.
- **IC > taxa crua:** reportar "11,8% [IC 10,9–12,9%]" e o IC da diferença (cruza zero?) decide melhor que comparar taxas soltas.
- **Cuidado com múltiplas métricas:** testar várias infla o falso positivo; a decisão se apoia na métrica primária pré-registrada, não em achados secundários garimpados.

---

*Os dados são sintéticos. O método é idêntico ao de um teste real — basta trocar pelos números
anonimizados da campanha.*

Os fundamentos usados aqui estão explicados passo a passo em
[`stats-foundations`](https://github.com/ghitflux/stats-foundations).

Hélcio Venâncio · [github.com/ghitflux](https://github.com/ghitflux) · Licença MIT
