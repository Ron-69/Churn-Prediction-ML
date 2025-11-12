# 🚀 Projeto de Previsão de Rotatividade de Clientes (Churn Prediction)

## Visão Geral

Este projeto demonstra a aplicação de Machine Learning (ML) para prever a probabilidade de rotatividade (churn) de clientes de uma empresa de telecomunicações. O objetivo é identificar clientes de alto risco para que a empresa possa implementar estratégias proativas de retenção.

## 🎯 Objetivo de Negócio

* Prever a variável binária **Churn** (Sim/Não) com alta precisão e sensibilidade.
* Identificar as **Features Mais Importantes** (Feature Importance) que influenciam a decisão do cliente de sair.

## 📈 Metodologia e Modelagem

O projeto seguiu o fluxo padrão de Data Science, com foco em tratar o desbalanceamento inerente ao problema de Churn.

### Etapas Principais:

1.  **Limpeza e EDA:** Tratamento de valores ausentes (NaN) e remoção de colunas irrelevantes (`customerID`). Análise da distribuição de `Churn` e tratamento de colunas como `TotalCharges`.
2.  **Pré-processamento:**
    * Codificação de variáveis categóricas via **One-Hot Encoding**.
    * Divisão dos dados em treino e teste (80/20) com **estratificação** (`stratify=y`).
    * **Escalonamento (StandardScaler)** das variáveis numéricas.
3.  **Modelagem:**
    * **Baseline:** Regressão Logística (para estabelecer a linha de base).
    * **Modelo Principal:** **Random Forest Classifier** (usando `class_weight='balanced'` para lidar com o desbalanceamento de classes).
4.  **Avaliação:** Uso de **Matriz de Confusão**, **F1-Score** e **ROC AUC** devido à natureza desbalanceada do dataset.

## ⚙️ Tecnologias e Dependências

* **Linguagem:** Python
* **Análise:** Pandas, NumPy
* **Visualização:** Matplotlib, Seaborn
* **Modelagem:** Scikit-learn (LogisticRegression, RandomForestClassifier, StandardScaler)
* **Ambiente:** Conda Environment (analise\_env) / Jupyter Notebook no VSCode

*(O arquivo `requirements.txt` lista todas as bibliotecas necessárias para reproduzir o ambiente.)*

## 🔑 Resultados Quantitativos e Insights (Atualizados)

A Regressão Logística foi o modelo com o melhor poder de discriminação geral (maior ROC AUC), mas o Random Forest forneceu o insight de negócio crucial sobre a importância das variáveis.

| Métrica | Regressão Logística (Baseline) | Random Forest (Melhor Desempenho) | Comentário |
| :--- | :--- | :--- | :--- |
| **ROC AUC** | **0.8359** | **0.8111** | O *baseline* teve maior poder de discriminação, mas ambos são fortes (> 0.80). |
| **F1-Score (Churn=1)** | **0.61** | **0.54** | F1-Score da Regressão Logística foi superior, indicando um melhor equilíbrio entre Precisão e Recall neste caso. |
| **Recall (Churn=1)** | 0.57 | 0.48 | Capacidade do modelo de identificar clientes que saíram. |

### Top 3 Fatores de Risco (Feature Importance - Modelo Random Forest):

A análise do Random Forest identificou os fatores de maior impacto no Churn:

1.  **TotalCharges** (0.143): O valor total gasto pelo cliente.
2.  **tenure** (0.129): O tempo em meses que o cliente permaneceu na empresa.
3.  **MonthlyCharges** (0.121): O valor da cobrança mensal.

**Insight de Negócio:** As três variáveis numéricas que representam o **Valor de Vida do Cliente (CLV)** e a **Longevidade** são os preditores mais fortes de rotatividade. Clientes que estão na empresa há pouco tempo ou que têm baixo CLV são de altíssimo risco.