# MVP - Machine Learning
## Previsão de Custos de Seguro de Saúde

### Autora
Natalia Simões

---

# 1. Objetivo do Projeto

Este projeto foi desenvolvido como parte do MVP da disciplina de Machine Learning da Pós-Graduação em Ciência de Dados e Analytics da PUC-Rio.

O objetivo é desenvolver modelos de Machine Learning capazes de prever os custos de seguros de saúde (`charges`) com base em características demográficas, comportamentais e clínicas dos segurados.

O problema foi tratado como uma tarefa de **Regressão Supervisionada**, uma vez que o objetivo consiste em prever uma variável numérica contínua.

---

# 2. Dataset

Foi utilizado o dataset **Health Insurance Cost Prediction Dataset**, disponível no Kaggle.

**Fonte:**
https://www.kaggle.com/

### Características da Base

- Aproximadamente 1 milhão de registros
- Dados sintéticos gerados para fins educacionais e experimentais
- Variável alvo: `charges`

### Principais Variáveis

| Variável | Descrição |
|-----------|-----------|
| age | Idade do segurado |
| gender | Sexo |
| bmi | Índice de Massa Corporal |
| children | Número de dependentes |
| smoker | Indica se o segurado é fumante |
| region | Região de residência |
| medical_history | Histórico médico |
| family_medical_history | Histórico médico familiar |
| exercise_frequency | Frequência de exercícios |
| occupation | Ocupação |
| coverage_level | Nível de cobertura contratada |
| charges | Custo do seguro (variável alvo) |

---

# 3. Análise Exploratória dos Dados

A análise exploratória permitiu compreender a distribuição das variáveis e identificar fatores relacionados ao custo do seguro.

Principais achados:

- Segurados fumantes apresentam custos significativamente superiores aos não fumantes.
- O nível de cobertura contratado possui forte influência sobre o valor do seguro.
- Histórico médico e histórico familiar também demonstraram impacto relevante.
- Idade, IMC e quantidade de dependentes apresentaram influência moderada.
- Foram identificados valores ausentes em algumas variáveis categóricas, tratados durante o pré-processamento.

---

# 4. Pré-processamento

As seguintes etapas foram aplicadas:

### Tratamento de valores ausentes
- Imputação utilizando a categoria mais frequente.

### Variáveis categóricas
- Transformação utilizando OneHotEncoder.

### Variáveis numéricas
- Padronização utilizando StandardScaler.

### Pipeline
- Utilização de Pipeline e ColumnTransformer para garantir reprodutibilidade e evitar vazamento de dados (Data Leakage).

---

# 5. Modelos Avaliados

Foram comparados três algoritmos de regressão:

### Baseline
- Regressão Linear

### Modelos candidatos
- Árvore de Decisão
- Random Forest

---

# 6. Avaliação dos Modelos

Os modelos foram avaliados utilizando:

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- R² (Coeficiente de Determinação)

## Resultados

| Modelo | R² |
|----------|----------|
| Regressão Linear | 0,8287 |
| Random Forest | 0,8071 |
| Random Forest Otimizado | 0,8075 |
| Árvore de Decisão | 0,6430 |

---

# 7. Otimização de Hiperparâmetros

Foi realizada uma etapa de otimização utilizando:

- RandomizedSearchCV
- Validação cruzada de 3 folds (`cv=3`)

Parâmetros avaliados:

- Número de árvores (`n_estimators`)
- Profundidade máxima (`max_depth`)
- Número mínimo de amostras para divisão (`min_samples_split`)

A otimização não gerou ganhos relevantes em relação ao modelo original.

---

# 8. Principais Resultados

- A Regressão Linear apresentou o melhor desempenho geral.
- Modelos mais complexos não superaram o baseline.
- Não foram observados sinais relevantes de overfitting ou underfitting.
- O modelo selecionado apresentou boa capacidade de generalização.
- O pipeline garantiu consistência e reprodutibilidade dos experimentos.

---

# 9. Limitações

- O dataset utilizado é sintético e foi criado para fins educacionais.
- Algumas variáveis importantes para a precificação real de seguros não estão presentes na base.
- Os resultados não devem ser utilizados diretamente em processos reais de subscrição ou precificação.

---

# 10. Conclusão

O projeto demonstrou a aplicação completa de um fluxo de Machine Learning para um problema de regressão, abrangendo análise exploratória, pré-processamento, modelagem, otimização e avaliação dos resultados.

Entre os modelos avaliados, a Regressão Linear apresentou o melhor desempenho, alcançando R² de aproximadamente 0,83 e superando algoritmos mais complexos. Os resultados mostram que, para este conjunto de dados, modelos simples e interpretáveis foram capazes de capturar adequadamente os padrões existentes.

Além dos resultados preditivos obtidos, o trabalho evidenciou a importância da preparação adequada dos dados, da utilização de pipelines reprodutíveis e da comparação sistemática entre diferentes algoritmos para a seleção do modelo mais adequado.

---

# Tecnologias Utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Scikit-Learn
- Google Colab

---

# Estrutura do Repositório

```text
├── MVP_Machine_Learning.ipynb
├── README.md
└── imagens/
```
