# Detecção de Fraude - Comparativo de Algoritmos de Árvore de Decisão e IA Generativa usando AutoEncoder

Este projeto busca criar um modelo preditivo que identifica transações com maior probabilidade de serem fraudulentas. Para isso, utilizamos tanto algoritmos tradicionais de machine learning (como Decision Trees e LightGBM) quanto técnicas de Inteligência Artificial Generativa, como o AutoEncoder.

## Estrutura do Projeto

### 1. `modelo_deteccao_fraude.ipynb`
#### Objetivo:
Criar um modelo preditivo para identificar fraudes transacionais.

#### Análise dos Dados:
- **Base de dados**: 284.807 transações, das quais 492 são fraudulentas (taxa de fraude de 0,17%).
- **Variáveis**:
  - **Time**: Tempo em segundos desde a primeira transação.
  - **V1 a V28**: Resultados de um PCA aplicado a diversas variáveis preditivas.
  - **Amount**: Valor da transação.
  - **Class**: Define se a transação foi fraudulenta (1) ou não (0).

A base não possui valores ausentes e, como os algoritmos utilizados são baseados em árvores com controle de overfitting (e.g. número mínimo de casos nas folhas), não foram realizados ajustes para outliers.

#### Modelagem:
Foram criados três modelos usando as seguintes técnicas:
1. **Decision Tree**
2. **LightGBM**
3. **XGBoost**

A melhor performance foi obtida com o LightGBM, embora apresentasse tendência a overfitting. A performance foi verificada em duas bases de teste distintas, separadas usando a variável Time:
- **Treino**: 80% dos primeiros casos.
- **Teste 1**: Próximos 10% dos casos.
- **Teste 2**: Últimos 10% dos casos.

#### Resultados:
- O LightGBM, embora perca performance da base de treino para as de teste, detecta 63% dos casos de fraude, impactando apenas 0,0527% das transações no pior cenário.
- Conclusão: O LightGBM é o modelo mais adequado para uso, dado o monitoramento contínuo.

---

### 2. `otimizacao_hiperparametros_optuna_ia_generativa.ipynb`
#### Objetivo:
Otimizar os hiperparâmetros do AutoEncoder usando o Optuna.

#### Resultados:
O código realiza simultaneamente a otimização dos hiperparâmetros e o feature selection. Ambas as saídas são usadas posteriormente no código principal de modelagem.

---

### 3. `modelo_deteccao_fraude_ia_generativa.ipynb`
#### Objetivo:
Desenvolver um modelo desafiador ao LightGBM, usando o AutoEncoder.

#### Abordagem:
O AutoEncoder trabalha comprimindo e, em seguida, reconstruindo as variáveis preditivas, tentando recriar as originais. O "score" é definido pela diferença entre as variáveis originais e as recriadas, e, por isso, todas as variáveis são normalizadas.

- O AutoEncoder é treinado apenas com transações não fraudulentas. Quando aplicado em transações fraudulentas, espera-se um erro de reconstrução maior.
- Utilizou-se o Optuna para otimizar os hiperparâmetros e realizar o feature selection, que foi comparado com a abordagem de Forward Feature Selection.

#### Resultados:
- O AutoEncoder conseguiu separar as transações fraudulentas das não fraudulentas, porém com performance inferior ao LightGBM.
- O feature selection feito pelo Optuna teve resultados inferiores ao Forward Feature Selection.

#### Conclusão:
As técnicas clássicas de machine learning, como o LightGBM, mostraram-se mais eficientes para este conjunto de dados. Além disso, o feature selection com Optuna não foi tão eficaz quanto o Forward Feature Selection.

---

## Requisitos

Este projeto utiliza as seguintes bibliotecas:

- `pandas`
- `scikit-learn`
- `xgboost`
- `lightgbm`
- `keras`
- `optuna`

## Como Utilizar

O projeto contém três notebooks que devem ser executados na seguinte ordem:
1. **modelo_deteccao_fraude.ipynb**: Criação do modelo baseado em técnicas tradicionais de machine learning.
2. **otimizacao_hiperparametros_optuna_ia_generativa.ipynb**: Otimização de hiperparâmetros e feature selection para o AutoEncoder.
3. **modelo_deteccao_fraude_ia_generativa.ipynb**: Criação e comparação do AutoEncoder com o modelo anterior.

## Autor

Este projeto foi desenvolvido por **Rafael Nunes de Oliveira**.
