# Classificação de Veículos - Financiamento

Este projeto tem como objetivo criar um modelo preditivo para o produto de financiamento de veículos, visando prever a inadimplência dos clientes com base em variáveis como renda, limite de cartão, entre outros. Testamos diversos algoritmos de machine learning, com destaque para o uso de LightGBM, XGBoost e Árvore de Decisão.

## Objetivo do Projeto

O foco do modelo preditivo é identificar quais clientes podem estar inadimplentes (30 dias ou mais de atraso) após 3 meses da contratação do financiamento, uma métrica conhecida como "TARGET_M3OVER30". Esse modelo auxilia a instituição financeira na tomada de decisão ao conceder crédito, reduzindo riscos de inadimplência.

## Descrição dos Dados

- **Tamanho da Base**: 7000 observações.
- **Período**: Entre os meses de outubro/2021 e dezembro/2021.
- **Taxa de maus**: 28% de inadimplência.
  
Durante a fase de pré-processamento, foram realizados ajustes e exclusões de variáveis, como a remoção das variáveis "idade" (devido a inconsistências) e "score de mercado" (por custo e baixa correlação com a inadimplência).

### Observação Importante

Há clientes com múltiplos empréstimos num curto período de tempo, o que levanta questões sobre a adequação da política de concessão de crédito, visto que essas características aparecem como fortes determinantes de inadimplência.

## Divisão de Dados

- **Base de Treino**: Meses de 10/21 e 11/21.
- **Base de Teste**: Mês de 12/21.

## Algoritmos Testados

Foram testados os seguintes algoritmos para a modelagem preditiva:

1. **Árvore de Decisão**
2. **LightGBM**
3. **XGBoost**

Os três algoritmos apresentaram resultados similares em termos de KS (Kolmogorov-Smirnov) e AUC (Área sob a Curva ROC). No entanto, optou-se por seguir com o modelo de **Árvore de Decisão** devido à sua maior interpretabilidade.

## Resultados e Insights

### Desempenho do Modelo

Os melhores nós da árvore de decisão indicaram que os clientes com renda baixa ou nula e os que possuem limites de cartão reduzidos apresentam as maiores taxas de inadimplência.

Exemplo de nós mais arriscados:
- **Renda <= 1535.83 & Limite Cartão <= 3357.18**
- **Renda <= 1535.83 & Limite Cartão > 3357.18**
- **Renda > 5431.54 & Limite Cartão <= 29.67**

Esses resultados sugerem que critérios como renda mínima e limite de crédito podem ser incorporados nas políticas de crédito da empresa.

### Considerações Finais

Embora o modelo atual tenha sido bem-sucedido, sua performance encontra-se no limite aceitável. Portanto, sugerimos que o desempenho do modelo seja monitorado ao longo do tempo, e que novas fontes de dados sejam exploradas para aumentar a robustez do modelo e reduzir a volatilidade dos resultados.

## Como Utilizar o Código

O projeto contém um único arquivo Jupyter Notebook:

- **classificacao_veiculos_modelo.ipynb**: Contém todo o fluxo de pré-processamento, modelagem e avaliação de performance.

Para rodar o projeto, basta abrir o arquivo `.ipynb` e seguir o fluxo proposto, utilizando as bibliotecas mencionadas abaixo.

## Requisitos

O projeto depende das seguintes bibliotecas:

- `pandas`
- `scikit-learn`
- `xgboost`
- `lightgbm`
- `numpy`
  
## Autoria

Este projeto foi desenvolvido por **Rafael Nunes de Oliveira**.

