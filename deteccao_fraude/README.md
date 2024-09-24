# Detecção de Fraude - Comparativo de Algoritmos de Árvore de Decisão e IA Generativa usando AutoEncoder

## Descrição do Projeto
Este projeto tem como objetivo desenvolver modelos de detecção de fraudes em transações financeiras. Para isso, dois enfoques são utilizados: algoritmos de Árvores de Decisão e IA Generativa com AutoEncoder. O projeto inclui um comparativo de performance entre esses dois tipos de abordagem. Além disso, foi incorporado o Optuna para otimizar os hiperparâmetros e selecionar as melhores features no AutoEncoder.

## Estrutura do Projeto

O projeto é organizado em três arquivos principais:

1. **1_modelo_deteccao_fraude.ipynb**: Cria um modelo de detecção de fraudes utilizando algoritmos de Árvores de Decisão. Este arquivo serve como baseline para o comparativo com o modelo de IA Generativa.

2. **2_otimizacao_hiperparametros_optuna_ia_generativa.ipynb**: Este arquivo utiliza o Optuna para realizar a otimização dos hiperparâmetros e a seleção de features mais importantes para o modelo baseado em AutoEncoder.

3. **3_modelo_deteccao_fraude_ia_generativa.ipynb**: Cria o modelo baseado em IA Generativa usando AutoEncoder. São implementados dois algoritmos:
   - O primeiro realiza a seleção de features com base no método **Forward Feature Selection**.
   - O segundo utiliza as features que o Optuna identificou como mais adequadas.

## Requisitos
Para executar este projeto, você precisará das seguintes bibliotecas:

- `numpy`
- `pandas`
- `scikit-learn`
- `tensorflow`
- `keras`
- `optuna`
- `lightgbm`
- `xgboost`
- `ydata_profiling`

### Instalação dos Requisitos

Para instalar as bibliotecas necessárias, você pode rodar:

```bash
pip install numpy pandas scikit-learn tensorflow keras optuna lightgbm xgboost ydata_profiling
