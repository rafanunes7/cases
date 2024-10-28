# Modelo de Previsão de Vendas com LightGBM e Prophet

## 1. Introdução

**Objetivo do Modelo:**  
O objetivo deste modelo é prever vendas de produtos baseando-se no histórico de vendas. As técnicas utilizadas foram tanto o LightGBM (Regressor) como  Prophet, de forma a termos um comparativo de performances.

---

## 2. Dados Utilizados

**Fonte dos Dados:**  
Os dados utilizados se encontram no arquivo 'vendas.csv', que tem em cada linha a quantidade de vendas de cada produto (sku) por dia.

**Variáveis do Conjunto de Dados:**
- `sku`: Identificador único do produto.
- `data_venda`: Data de cada observação de vendas.
- `venda`: Quantidade de vendas observadas.

**Pré-processamento dos Dados:**
- **Completude**: A base de dados possui "buracos", ou seja nem todos os dias possui vendas para todos os produtos. O ajuste realizado assegura que isso seja corrigido, imputando o valor 0 aos dias sem informações (partindo do pressuposto que foi um dia sem vendas e não um erro de base).
- **Criação de variáveis**: Criação de features para capturar tendências temporais e variações sazonais.
- **Split de dados**: Divisão dos dados em treino e teste para avaliação do modelo.

---

## 3. Modelos Utilizados

### Modelo 1: LightGBM
- **Descrição**: O LightGBM é um algoritmo de boosting baseado em árvores de decisão, utilizado para prever vendas com base nas variáveis históricas e nos dados dos produtos.
- **Otimização**:
  - **Optuna**: Utilizado para encontrar os melhores hiperparâmetros do LightGBM, como número de árvores, taxa de aprendizado, e fração de amostras.
  - **Forward Feature Selection**: Processo iterativo de seleção de variáveis para escolher as features mais relevantes para o modelo.

### Modelo 2: Prophet
- **Descrição**: Prophet é um modelo de séries temporais desenvolvido para capturar padrões sazonais e tendências em dados históricos de maneira prática e intuitiva. Ao contrário do LightGBM, o Prophet não requer muitos ajustes de hiperparâmetros e lida bem com dados sazonais.
- **Ajuste Sazonal**: Por ser um modelo de série temporal, o Prophet é configurado para capturar diretamente as variações sazonais e tendências dos dados de vendas, sem a necessidade de seleção de variáveis adicionais.

---

## 4. Prós e Contras dos Modelos

| Modelo       | Prós                                                                                           | Contras                                                                                  |
|--------------|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **LightGBM** | - Excelente para dados com múltiplas variáveis preditivas.<br>- Possui alta flexibilidade com otimização via Optuna e seleção de variáveis.<br>- Bom desempenho computacional em dados tabulares. | - Não captura sazonalidade automaticamente.<br>- Requer a criação de variáveis reditivas, além do ajuste de hiperparâmetros para otimização, aumentando a complexidade. |
| **Prophet**  | - Capta automaticamente tendências e sazonalidade nos dados.<br>- Fácil de implementar, sem necessidade de ajuste de hiperparâmetros.<br> | - Precisa de um modelo separado para cada produto (`sku`), dificultando o gerenciamento e a governança.<br>- Não dá muita margem para melhora do desempenho. |

---

## 5. Treinamento dos Modelos

**Procedimento de Treinamento:**

### LightGBM
1. **Seleção de Variáveis**: Utilização do método de Forward Feature Selection para escolher as variáveis mais relevantes para o modelo.
2. **Otimização de Hiperparâmetros**: Utilização do Optuna para ajustar os hiperparâmetros do modelo e maximizar o desempenho preditivo.
3. **Treinamento do Modelo**: O LightGBM é treinado utilizando os dados de treino, considerando as variáveis selecionadas e os hiperparâmetros otimizados.

### Prophet
1. **Treinamento Simples**: O Prophet é aplicado diretamente sobre a série temporal de vendas de cada `sku`.
2. **Captura de Padrões**: O modelo ajusta automaticamente a sazonalidade e as tendências para cada série temporal sem necessidade de ajustes complexos de hiperparâmetros e prevê a venda dos próximos dias.

---

## 6. Avaliação dos Modelos

**Métricas Utilizadas:**
**MAE (Mean Absolute Error)**: Média dos erros absolutos, útil para entender a precisão média das previsões.

**Desempenho dos Modelos:**
- **LightGBM**: Com os ajustes de hiperparâmetros e seleção de variáveis, o LightGBM demonstrou ótimo desempenho, obtendo um MAE de 21,17 na base de testes. 
- **Prophet**: Demonstrou excelente capacidade de capturar a sazonalidade e as tendências temporais, mesmo sem qualquer necessidade de criaçaõ de variáveis preditivas prévias. Porém teve resultados piores que o LightGBM, alcançando um MAE de 36,34.

---

## 7. Limitações e Melhorias Futuras

**Limitações:**
- **LightGBM**: Limitações para captura de sazonalidade automática, requerendo mais ajustes manuais.
- **Prophet**: Complexidade em gerenciar múltiplos modelos para diferentes produtos (`sku`), especialmente para um grande número de itens.

**Possíveis Melhorias:**
- **Automatização do Gerenciamento de Modelos**: Implementar um sistema que permita treinar e gerenciar múltiplos modelos Prophet para diferentes `sku`s de forma mais eficiente.
- **Integração de Modelos Híbridos**: Explorar combinações entre LightGBM e modelos de séries temporais para capturar tanto variáveis auxiliares quanto sazonalidade de forma conjunta.

---

## 8. Conclusão

Os resultados mostram que quando existe a possibilidade (sob a ótica de tempo e de processamento) de criação de variáveis preditivas, o LightGBM traz um melhor resultado. Com isso dito, para análises mais rápidas o Prophet pode ser uma solução viável.

---

## 9. Contato e Manutenção

**Responsável:** Rafael Nunes de Oliveira  
**Contato:** rafaelnoliveira@outlook.com 