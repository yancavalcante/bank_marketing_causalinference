# bank_marketing_causalinference
Bank Marketing Causal Inference is a project which aims to infer the most important causes of the deposits on a fictional bank


# 📊 Bank Marketing Causal Inference

Este projeto tem como objetivo identificar os principais **determinantes causais** para a adesão de clientes a depósitos a prazo em um banco português, a partir dos dados de campanhas de marketing.

## 🎯 Objetivo
Diferente de uma análise puramente preditiva, aqui o foco está em **inferir relações causais**: entender **o que de fato causa um cliente a aderir ao depósito**, e não apenas correlacionar variáveis.

## 📂 Estrutura do projeto
- `Bank_Marketing_Causal_Inference.ipynb`: Notebook principal contendo:
  - **EDA (Análise Exploratória de Dados)** com foco em inferência causal;
  - Construção de hipóteses e DAGs (causal graphs);
  - Estimativa de efeitos causais com diferentes métodos (`DoWhy`);
  - Visualizações (taxas de adesão, forest plots);
  - Testes de robustez (refutadores).
-`bank-additional-full.csv`: Dataset utilizado no projeto, contendo 41188 linhas × 21 colunas

## 📦 Bibliotecas utilizadas
- [pandas](https://pandas.pydata.org/) para manipulação de dados;  
- [seaborn](https://seaborn.pydata.org/) e [matplotlib](https://matplotlib.org/) para visualização;  
- [DoWhy](https://microsoft.github.io/dowhy/) para modelagem causal;  
- [scikit-learn](https://scikit-learn.org/) para suporte a matching e regressão.

## 📊 Dataset
Os dados utilizados são do **UCI Bank Marketing Dataset**, que contém:
- Informações demográficas e financeiras dos clientes (idade, profissão, escolaridade, saldo, etc.);
- Variáveis relacionadas às campanhas de marketing (mês, número de contatos, resultado de campanhas anteriores);
- Variável alvo `y`, que indica se o cliente **assinou** ou não o depósito a prazo.

## 🔎 Principais análises
- **Taxa de adesão** por grupos de tratamento (`poutcome_success`, `month_oct`, `previous_bin`);
- Estimativas de efeito causal com:
  - **Propensity Score Matching (PSM)** para tratamentos binários;
  - **Regressão Linear (backdoor.linear_regression)** para variáveis contínuas;
- **Forest plots** com intervalos de confiança (IC95%);
- Refutação de estimativas usando placebo e confundidores aleatórios.

## 📌 Principais achados
- **Sucesso anterior (`poutcome_success`)** e **campanhas realizadas em março (`month_mar`)** aparecem como os fatores mais fortemente associados à adesão, com efeitos estimados robustos.
- A variável **(`poutcome_success`)** apresenta efeito positivo fraco e significativo (ATE ≈ 0,15), indicando que clientes com histórico de sucesso têm probabilidade substancialmente maior de aderir novamente ao depósito.
- A variável **(`month_mar`)** também exibem efeito positivo e estatisticamente significativo (ATE ≈ 0,28), sugerindo um padrão sazonal favorável nesse período.
- O histórico de contato binário **(`previous_bin`)**: efeito negativo e estatisticamente significativo (ATE ≈ -7,62), porém anômalo, possível multicolinearidade.
- O número de contatos anteriores (`previous`) mostrou efeito praticamente nulo.

## ⏭️ Próximos passos
- Testar a hipótese de multicolinearidade no histórico de contato binário
- Realizar a conclusão e formular diretrizes para possíveis stakeholders

## ▶️ Como executar
1. Clone este repositório:
   ```bash
   git clone https://github.com/yancavalcante/bank_marketing_causalinference.git
