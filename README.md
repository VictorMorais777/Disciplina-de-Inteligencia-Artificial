# Disciplina de Inteligência Artificial

Repositório com os notebooks, exercícios e trabalhos desenvolvidos na disciplina de **Inteligência Artificial** do curso de **Engenharia de Software** (Universidade de Mogi das Cruzes).

O repositório registra a evolução ao longo da disciplina: começa em **Python e lógica de programação**, passa por **análise de dados** com NumPy, Pandas, Matplotlib e SciPy e chega a **Machine Learning** com scikit-learn (SVM, árvores de decisão, florestas aleatórias e boosting).

## 📁 Estrutura do repositório

| Arquivo | Tema | Tipo de problema |
| --- | --- | --- |
| [`Exercícios_Python_JoaoVictorSilvaMorais_Engenharia_de_Software_6B.ipynb`](./Exerc%C3%ADcios_Python_JoaoVictorSilvaMorais_Engenharia_de_Software_6B.ipynb) | Exercícios de Python (1–50) | Lógica de programação |
| [`DataScience_JoaoVictorSilvaMorais_Engenharia_de_Software_Noturno_6B.ipynb`](./DataScience_JoaoVictorSilvaMorais_Engenharia_de_Software_Noturno_6B.ipynb) | NumPy, Pandas, Matplotlib e SciPy | Análise de dados |
| [`vendas.xlsx`](./vendas.xlsx) | Planilha de vendas usada no notebook de Data Science | Base de dados |
| [`avalia-o-iris-com-svm (1).ipynb`](./avalia-o-iris-com-svm%20(1).ipynb) | SVM no dataset Iris | Classificação |
| [`joaovictordasilvademorais-arvore-de-decis-o-ipynb.ipynb`](./joaovictordasilvademorais-arvore-de-decis-o-ipynb.ipynb) | SVM, Árvore de Decisão, Floresta Aleatória e AdaBoost no Iris | Classificação (comparação de modelos) |
| [`joaovictordasilvademorais-svm-ipynb.ipynb`](./joaovictordasilvademorais-svm-ipynb.ipynb) | SVR no dataset Housing | Regressão |
| [`FISHMORPH_Dataset.ipynb`](./FISHMORPH_Dataset.ipynb) | SVM com Grid Search no dataset FISHMORPH | Classificação de famílias de peixes |

---

## 🐍 Exercícios de Python

Notebook com 50 exercícios, de conceitos básicos a algoritmos um pouco mais elaborados.

**Conceitos praticados:**

* Variáveis, tipos de dados, entrada e saída
* Estruturas condicionais (`if`, `elif`, `else`) e de repetição (`for`, `while`)
* Listas, dicionários, strings e matrizes
* Funções e funções recursivas
* Busca e ordenação (busca binária, Bubble Sort e Insertion Sort)

**Exemplos de exercícios:** fatorial, tabuada, Fibonacci, números primos, palíndromos, anagramas, validação de CPF, Cifra de César, calculadora simples, FizzBuzz, gerador de senhas, Jogo da Forca, Jogo da Velha, jogo de dados, remoção de duplicatas, contagem de frequência, média e desvio padrão, soma dos dígitos e gráficos de barras.

**Bibliotecas:** `random`, `string` e `matplotlib`. Os exercícios de estatística também foram resolvidos com recursos do próprio Python, sem bibliotecas externas.

## 📊 Data Science

Notebook com exercícios de análise e computação científica.

* **NumPy e Pandas:** manipulação de arrays e DataFrames, leitura de arquivos CSV e Excel (`vendas.xlsx`) e agrupamentos com `groupby`
* **Matplotlib:** histogramas, gráficos de dispersão e outras visualizações
* **Estatística:** medidas como a moda, com `statistics.mode`
* **SciPy:**
  * integração (`integrate`, `solve_ivp`)
  * interpolação (`interpolate`)
  * otimização e ajuste de curvas (`optimize`, `minimize`, `curve_fit`)
  * álgebra linear (`det`, `inv`, `solve`, `eig`)
  * transformada de Fourier (`fft`, `ifft`)

## 🤖 Machine Learning

Os trabalhos de Machine Learning usam **scikit-learn** e seguem, em geral, o mesmo fluxo: análise exploratória, preparação dos dados, divisão treino/teste, treinamento, otimização de hiperparâmetros com `GridSearchCV` e avaliação.

### 1. Avaliação do Iris com SVM

Classificação das espécies de flor do dataset **Iris** com `SVC`.

* Análise exploratória, preparação dos dados (`StandardScaler`, `LabelEncoder`), criação do modelo e avaliação
* Métricas: acurácia, `classification_report` e matriz de confusão
* **Resultado:** acurácia de **96,67%** no conjunto de teste. A *Iris-setosa* foi classificada sem erros, e as confusões ocorrem entre *Iris-versicolor* e *Iris-virginica*

### 2. Comparação de modelos no Iris

Comparação de quatro classificadores no dataset **Iris**, cada um em duas condições: **sem** e **com** `GridSearchCV`.

| Modelo | Hiperparâmetros testados no Grid Search |
| --- | --- |
| SVM (`SVC`) | `C` e `kernel` (linear e rbf, com `gamma` em `scale` e `auto`) |
| Árvore de Decisão | `criterion`, `max_depth` e `min_samples_split` |
| Floresta Aleatória | `n_estimators`, `criterion`, `max_depth` e `min_samples_split` |
| AdaBoost | `n_estimators` e `learning_rate` |

* Validação cruzada com `cv=5`
* Métricas: acurácia e sensibilidade (recall), além da tabela comparativa e da análise do efeito da otimização de hiperparâmetros

### 3. SVR com o dataset Housing

Problema de **regressão** com `SVR` para prever valores de imóveis, usando o dataset **Housing** (20.640 linhas e 10 colunas).

* Tratamento de valores ausentes (`SimpleImputer`) e padronização (`StandardScaler`)
* `GridSearchCV` com `C`, `epsilon`, `gamma` e `kernel`
* Métricas: R², MAE e MSE

### 4. FISHMORPH: classificação de famílias de peixes

Classificação da **família** de peixes a partir de 10 medidas morfológicas (`MBl`, `BEl`, `VEp`, `REs`, `OGp`, `RMl`, `BLs`, `PFv`, `PFs` e `CPt`), usando o dataset **FISHMORPH** (8.342 registros e 197 famílias).

**Etapas:**

1. Importação do dataset
2. Análise dos dados: verificação de nulos e remoção de duplicatas
3. Visualização da distribuição das categorias
4. Divisão treino/teste e validação cruzada (`cv=5`)
5. `GridSearchCV` em um `Pipeline` (`StandardScaler` + `SVC`), testando 4 valores para cada hiperparâmetro:
   * `kernel`: `linear`, `poly`, `rbf` e `sigmoid`
   * `C`: 0,1, 1, 10 e 100
   * `gamma`: 0,001, 0,01, 0,1 e 1
6. Melhor modelo, melhores parâmetros e acurácia (validação cruzada e teste)
7. Acurácia e matriz de confusão

## 🛠️ Tecnologias e ferramentas

* **Python**
* **Google Colab** e **Kaggle Notebooks**
* **GitHub**
* Bibliotecas: `numpy`, `pandas`, `matplotlib`, `seaborn`, `scipy` e `scikit-learn`

## 🎯 Objetivo

Registrar e demonstrar a evolução no aprendizado de programação e de Inteligência Artificial ao longo da disciplina. Os notebooks buscam compreender não só o funcionamento do código, mas também a lógica e o raciocínio por trás de cada solução.

## 👨‍💻 Autor

**João Victor da Silva de Morais**

Curso: **Engenharia de Software**

Disciplina: **Inteligência Artificial**
