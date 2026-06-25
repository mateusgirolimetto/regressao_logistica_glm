# Regressão Logística Binária com glm

Modelo de regressão logística binária ajustado com a função `glm` do R base para prever o diagnóstico de diabetes a partir de variáveis clínicas e sociodemográficas.

## Conteúdo

- `Regressão Logística Binária com glm.Rmd`: script em R Markdown com todo o pipeline de análise.

## Pipeline da análise

1. **Carregamento e pré-processamento**: leitura do dataset e conversão de variáveis categóricas em fatores (sexo, etnia, escolaridade, renda, status de emprego, tabagismo, histórico familiar, entre outras).
2. **Divisão treino/validação/teste**: separação em 95% treino e 5% teste; o conjunto treino é subdividido em 85% treino final e 10% validação.
3. **Padronização**: variáveis numéricas padronizadas (média e desvio) com base no treino e aplicadas ao teste, evitando vazamento de dados.
4. **Ajuste do modelo GLM logístico**: modelo ajustado com `glm(..., family = binomial)` excluindo as variáveis `diabetes_stage` e `diabetes_risk_score`.
5. **Definição do limiar**: curva ROC calculada no conjunto de validação; limiar escolhido para garantir sensibilidade ≥ 0.90.
6. **Avaliação final**: modelo re-treinado em todo o conjunto treino e avaliado no teste com matriz de confusão e AUC.

## Requisitos

- R (versão recente)
- Pacotes: `readr`, `caret`, `dplyr`, `pROC`

## Autor

Mateus V. Girolimetto
