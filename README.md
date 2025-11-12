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

## 🔑 Resultados (Atualize com Seus Valores)

| Métrica | Regressão Logística (Baseline) | Random Forest (Melhor Desempenho) | Comentário |
| :--- | :--- | :--- | :--- |
| **ROC AUC** | 0.8359 | **[Valor da Célula 11]** | Excelente poder discriminatório. |
| **F1-Score (Churn=1)** | 0.61 | **[Valor da Célula 11]** | Métrica chave para dados desbalanceados. |
| **Recall (Churn=1)** | 0.57 | **[Valor da Célula 11]** | Indica a capacidade de capturar clientes que vão sair. |

### Top 3 Fatores de Risco (Feature Importance):

1.  **[1ª Feature da Célula 12]**
2.  **[2ª Feature da Célula 12]**
3.  **[3ª Feature da Célula 12]**