# Collection Score - Financiamento

Este projeto tem como objetivo desenvolver um modelo preditivo para recuperação de financiamento de veículos, auxiliando na definição de estratégias de cobrança mais eficazes e na otimização de recursos. O modelo segmenta os clientes com base no comportamento de pagamento, permitindo ações direcionadas para redução da inadimplência.

## Objetivo do Projeto

Criar um modelo de classificação para prever o comportamento de pagamento dos clientes inadimplentes com base na variável resposta definida como:

- **MAU**: Cliente que não pagou nada da dívida.
- **INDETERMINADO**: Cliente que pagou até 50% da dívida.
- **BOM**: Cliente que pagou pelo menos 50% da dívida.

Para o treinamento do modelo, os clientes classificados como "INDETERMINADO" foram excluídos, pois podem introduzir ruído. Contudo, para a avaliação final, esses clientes foram considerados como "BOM". Testamos os algoritmos **Árvore de Decisão**, **LightGBM** e **XGBoost**, priorizando o modelo com maior interpretabilidade e performance.

## Descrição dos Dados

- **Tamanho da Base**: 300.000 casos.
- **Período**: Março de 2022 a Janeiro de 2023.
- **Taxa de maus**: 35%.

A base apresentou estabilidade na taxa de maus ao longo do período analisado. O pré-processamento incluiu:

1. **Tratamento de valores nulos**:
   - Imputação pela mediana para variáveis numéricas.
   - Criação de uma categoria própria para variáveis categóricas.
2. **Escalonamento (removido no modelo final)**:
   - O escalonamento por MinMax foi aplicado inicialmente, mas removido posteriormente, já que o modelo final escolhido (Árvore de Decisão) não depende de escalonamento e sua remoção favoreceu a interpretabilidade dos nós.

## Divisão de Dados

- **Base de Treino**: Março de 2022 a Setembro de 2022.
- **Base de Teste**: Outubro de 2022 a Janeiro de 2023.

## Modelagem e Resultados

Os algoritmos testados foram:

1. **Árvore de Decisão**
2. **LightGBM**
3. **XGBoost**

Os três algoritmos apresentaram resultados similares em termos de KS (Kolmogorov-Smirnov) e AUC-ROC (Área sob a Curva ROC), tanto na base de treino quanto na de teste. Por isso, optamos por utilizar o modelo de **Árvore de Decisão** devido à sua interpretabilidade e simplicidade operacional, evitando também a complexidade de monitorar múltiplos modelos.

### Insights do Modelo

Os resultados do modelo mostraram que:

- **Piores nós (alta inadimplência)**:
  - Clientes com **mais de 51 dias de atraso**.
  - Clientes cujas variáveis **`var_144 > 3`** e **`var_166 < 99.95`**, cujas interpretações de negócio ainda não foram esclarecidas.

- **Melhores nós (baixa inadimplência)**:
  - Clientes com **até 15 dias de atraso**.
  - **Idade** acima de **34 anos**.

Com base nesses resultados, os nós da árvore foram agrupados em **8 grupos homogêneos (GHs)**, permitindo uma segmentação mais clara e estratégias de cobrança direcionadas.

### Estratégia de Cobrança

Abaixo, as recomendações de ações com base nos grupos homogêneos (GHs):

| **Grupo Homogêneo (GH)** | **Taxa de Maus** | **Recomendações de Ação**                                      |
|---------------------------|------------------|----------------------------------------------------------------|
| **GH1 e GH2**             | Menor           | Ações leves: mensagens de SMS, e-mail ou lembretes.            |
| **GH3 a GH6**             | Intermediária   | Ações moderadas: chamadas telefônicas. Negativação em atrasos maiores, priorizando GH3 em relação a GH6. |
| **GH7 e GH8**             | Maior           | Ações severas: negativação imediata e envio para cobradora.     |

Essa abordagem permite otimizar custos, priorizar recursos e adotar estratégias mais assertivas para cada perfil de cliente.

## Considerações Finais

O modelo desenvolvido apresentou bons resultados, sendo capaz de segmentar a base de clientes em grupos homogêneos que suportam decisões de cobrança mais efetivas. Contudo, o desempenho ainda pode ser aprimorado, e algumas limitações precisam ser abordadas em estudos futuros.

### Próximos Passos

1. Aprofundamento dos estudos sobre os algoritmos **LightGBM** e **XGBoost**.
2. Exploração de modelos por faixa de atraso, avaliando o potencial de ganhos adicionais.
3. **Análise de estabilidade dos GHs** por safra de clientes.
4. **Análise de estabilidade das variáveis preditivas** para garantir robustez e confiabilidade do modelo ao longo do tempo.

## Como Utilizar o Código

O projeto contém um único arquivo Jupyter Notebook:

- **collection_score.ipynb**: Contém todo o fluxo de pré-processamento, modelagem e avaliação de performance.

Para executar o projeto, basta abrir o arquivo `.ipynb` e seguir o fluxo proposto, utilizando as bibliotecas mencionadas abaixo.

## Requisitos

O projeto depende das seguintes bibliotecas:

- `pandas`
- `numpy`
- `time`
- `re`
- `ydata_profiling`
- `scikit-learn`
- `optuna`
- `lightgbm`
- `xgboost`
- `matplotlib`

## Autoria

Este projeto foi desenvolvido por **Rafael Nunes de Oliveira**.
