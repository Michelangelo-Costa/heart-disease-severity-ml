# Documentação do Projeto: Classificação Multi-Classe de Doenças Cardíacas

![Python](https://img.shields.io/badge/Python-3.10%2B-blue)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange)
![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-green)
![Status](https://img.shields.io/badge/Status-Concluído-brightgreen)

## 📋 Informações Gerais

| Campo | Descrição |
| :--- | :--- |
| **Projeto** | Classificação Multi-Classe de Severidade de Doenças Cardíacas |
| **Disciplina** | Inteligência Artificial - SI-2023 |
| **Instituição** | Universidade Federal do Sul e Sudeste do Pará (UNIFESSPA) |
| **Professor** | Adam D. F. dos Santos |
| **Autores** | Michelangelo Costa, Igor Santos, André Santos, João Marcos |
| **Data** | Dezembro de 2025 |

## 🎯 Objetivo

Desenvolver e comparar modelos de **Machine Learning** para classificar a severidade de doenças cardíacas em 5 níveis (0 a 4), utilizando dados clínicos e laboratoriais. O projeto busca identificar padrões complexos para auxiliar no diagnóstico médico preditivo, focando na redução de falsos negativos (Recall).

## 📊 Dataset

### Heart Disease Dataset (UCI/Kaggle)

| Atributo | Valor |
| :--- | :--- |
| **Fonte** | [Heart Disease Dataset - Kaggle](https://www.kaggle.com/datasets/redwankarimsony/heart-disease-data) |
| **Registros** | 920 pacientes |
| **Variável Alvo** | `num` (Severidade da doença: 0 a 4) |

### Variáveis Utilizadas

| Variável | Descrição |
| :--- | :--- |
| `age` | Idade do paciente |
| `sex` | Sexo (Masculino/Feminino) |
| `cp` | Tipo de dor no peito (4 categorias) |
| `trestbps` | Pressão arterial em repouso (mm Hg) |
| `chol` | Colesterol sérico (mg/dl) |
| `fbs` | Açúcar no sangue em jejum (> 120 mg/dl) |
| `restecg` | Resultados eletrocardiográficos em repouso |
| `thalch` | Frequência cardíaca máxima alcançada |
| `exang` | Angina induzida por exercício |
| `oldpeak` | Depressão de ST induzida por exercício |
| `slope` | Inclinação do segmento ST no pico do exercício |
| `ca` | Número de vasos principais coloridos por fluoroscopia |
| `thal` | Cintilografia do miocárdio |

### Classes de Severidade (`num`)

- **0**: Ausência de doença
- **1**: Doença leve
- **2**: Doença moderada
- **3**: Doença severa
- **4**: Doença muito severa

## 🔧 Metodologia

### 1. Pré-processamento
- **Limpeza de Dados**: Tratamento de valores nulos e imputação de dados faltantes.
- **Normalização**: Aplicação de `StandardScaler` para padronização das features numéricas.
- **Divisão**: Separação em conjuntos de Treino e Teste.

### 2. Algoritmos Implementados

| Algoritmo | Responsável | Descrição |
| :--- | :--- | :--- |
| **Regressão Logística** | André Santos | Baseline linear e interpretável. |
| **Random Forest** | Igor Santos | Ensemble learning robusto a overfitting. |
| **SVM** | João Marcos | Busca de hiperplanos de separação ótimos. |
| **KNN** | Michelangelo Costa | Classificação baseada em proximidade. |

### 3. Otimização (Tuning)
Foi realizada a otimização de hiperparâmetros em **todos os modelos** (KNN, SVM, Regressão Logística e Random Forest) utilizando `GridSearchCV`. O objetivo foi refinar o desempenho de cada algoritmo, buscando as melhores configurações para maximizar métricas críticas como **Recall** e **F1-Score**.

## 📈 Métricas de Avaliação

- **Recall (Sensibilidade)**: Crucial para área médica (minimizar falsos negativos).
- **F1-Score**: Equilíbrio entre precisão e recall, especialmente útil para nossas classes desbalanceadas.
- **Acurácia**: Visão geral do desempenho do modelo.

## 📁 Estrutura do Projeto

heart-disease-severity-ml/
│
├── README.md # Documentação do projeto
└── Trabalho_Final_muilti_class.ipynb # Notebook principal com análises e modelos

## 🛠️ Dependências

pandas
numpy
matplotlib
seaborn
scikit-learn
kagglehub

## 🚀 Como Executar

1. **Clone o repositório**:

git clone https://github.com/Michelangelo-Costa/heart-disease-severity-ml.git

2. **Instale as dependências**:

pip install pandas numpy matplotlib seaborn scikit-learn kagglehub

3. **Execute o Notebook**:
Abra o arquivo `Trabalho_Final_muilti_class.ipynb` no Jupyter Notebook, VS Code ou Google Colab e execute as células sequencialmente.

---
Desenvolvido para a disciplina de Inteligência Artificial - UNIFESSPA 2025.
