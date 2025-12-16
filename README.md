# 🫀 Predição de Severidade de Doenças Cardíacas (Multi-Classe)

![Status](https://img.shields.io/badge/Status-Concluído-green) ![Python](https://img.shields.io/badge/Python-3.x-blue) ![Lib](https://img.shields.io/badge/Library-Scikit--Learn-orange)

## 📋 Informações Gerais

| Campo | Descrição |
| :--- | :--- |
| **Projeto** | Classificação Multi-Classe de Severidade Cardíaca |
| **Objetivo** | Predizer o nível da doença (0 a 4) com base em exames clínicos |
| **Modelos** | Random Forest, SVM, KNN, Regressão Logística |
| **Métrica Principal** | F1-Score (Macro) |
| **Autor** | [Seu Nome Aqui] |
| **Data** | Dezembro de 2025 |

---

## 🎯 Objetivo

Desenvolver um sistema de **Machine Learning** capaz de ir além do diagnóstico binário (Doente/Saudável), classificando a severidade da doença cardíaca em 5 níveis específicos para auxiliar na triagem e priorização médica.

> **Níveis de Severidade:**
> * `0`: Ausência de doença
> * `1`: Leve
> * `2`: Moderada
> * `3`: Severa
> * `4`: Muito Severa

---

## 📊 Dataset e Variáveis

O projeto utiliza um conjunto de dados clínicos contendo exames laboratoriais e sintomas.

### Variáveis Principais (Features)

| Variável | Descrição | Importância |
| :--- | :--- | :--- |
| **cp** | Tipo de dor no peito (Chest Pain) | ⭐ Alta |
| **thalach** | Frequência cardíaca máxima atingida | ⭐ Alta |
| **oldpeak** | Depressão do segmento ST induzida por exercício | ⭐ Alta |
| **ca** | Número de vasos principais coloridos por fluoroscopia | ⭐ Alta |
| **age** | Idade do paciente | Média |
| **chol** | Colesterol sérico (mg/dl) | Média |
| **trestbps** | Pressão arterial em repouso | Média |

---

## 🔧 Metodologia

### 1. Pré-processamento
* **Limpeza:** Tratamento de valores nulos e *outliers*.
* **Escalonamento:** Utilização do `StandardScaler` para normalizar as escalas (essencial para KNN e SVM).
* **Balanceamento:** Aplicação de pesos (`class_weight='balanced'`) para mitigar a escassez de dados nas classes 3 e 4.

### 2. Modelagem (4 Abordagens)

Testamos quatro algoritmos distintos para entender qual lida melhor com a complexidade multi-classe:

1.  **Regressão Logística Multinomial:** Baseline (modelo linear).
2.  **Random Forest Classifier:** Ensemble de árvores de decisão (Robusto a ruídos).
3.  **SVM (Kernel RBF):** Para encontrar fronteiras de decisão não-lineares.
4.  **KNN (K-Nearest Neighbors):** Classificação baseada na vizinhança local.

### 3. Otimização
Utilizamos **Grid Search** para encontrar os melhores hiperparâmetros (ex: melhor `K` para KNN, melhor `C` e `Gamma` para SVM).

---

## 📈 Resultados e Comparação

Após a validação cruzada (**5-Fold Cross-Validation**), os resultados foram:

| Algoritmo | F1-Score (Macro) | Estabilidade (Desvio Padrão) | Análise |
| :--- | :--- | :--- | :--- |
| **Random Forest** | **0.3406** | **± 0.0152** | 🏆 **Vencedor:** Melhor equilíbrio e estabilidade. |
| KNN | 0.3161 | ± 0.0322 | Instável (Alta variância entre testes). |
| Regressão Logística | 0.3178 | ± 0.0138 | Consistente, mas com performance limitada. |
| SVM | 0.3070 | ± 0.0265 | Sensível aos parâmetros. |

> **Por que F1-Macro?**
> Acurácia geral (~58%) é enganosa pois o modelo acerta muito as classes 0 e 1. O F1-Macro revela a dificuldade real em detectar as classes raras (3 e 4).

---

## 🧠 Conclusões e Insights

### 1. O Desafio da "Classe 4"
Todos os modelos tiveram dificuldade extrema em diferenciar **Severa (3)** de **Muito Severa (4)**.
* **Causa:** O dataset de teste continha apenas 6 exemplos da classe 4.
* **Comportamento:** O Random Forest optou por classificar esses casos como "Severa" ou "Moderada" para evitar falsos positivos aleatórios.

### 2. Random Forest é o mais seguro
Foi o único modelo que manteve a consistência (boxplots compactos) em todas as dobras da validação cruzada, tornando-o o mais confiável para produção.

### 3. Recomendação de Negócio
Sugere-se fundir as classes 3 e 4 em um alerta único de **"Alto Risco"**. Isso aumentaria significativamente a precisão prática da ferramenta para triagem hospitalar.

---

## 📁 Estrutura do Repositório

```text
heart-disease-severity-ml/
│
├── 📂 data
│   └── heart.csv                   # Dataset utilizado
│
├── 📂 notebooks
│   └── classification_analysis.ipynb # Código completo comentado
│
├── 📂 images
│   ├── matrix_confusao.png         # Heatmaps dos erros/acertos
│   ├── boxplot_comparison.png      # Comparação de estabilidade (CV)
│   └── accuracy_knn.png            # Curva de aprendizado do K
│
├── requirements.txt                # Bibliotecas necessárias
└── README.md                       # Documentação do projeto
