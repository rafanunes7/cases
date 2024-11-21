# Repositório de Projetos de Data Science e Machine Learning

Bem-vindo ao meu repositório de projetos! Aqui você encontrará uma coleção de projetos relacionados a **Data Science**, **Machine Learning** e **Inteligência Artificial**, com foco em **risco de crédito**, **fraude**, **previsão de vendas** e outros desafios analíticos.  

Cada projeto é descrito em detalhes em seu respectivo diretório, incluindo o código, as técnicas utilizadas e os insights extraídos.

---

## Estrutura do Repositório

Os projetos neste repositório estão organizados da seguinte forma:

### 1. **Recuperação de Crédito para Veículos**
- **Descrição:** Criação de um modelo preditivo para recuperação de financiamento de veículos. A abordagem classifica clientes em "Bom", "Indeterminado" ou "Mau" com base no pagamento da dívida, otimizando estratégias de cobrança.
- **Tecnologias Utilizadas:** Python, pandas, scikit-learn, LightGBM, Optuna.
- **Modelo Final:** Árvore de Decisão com agrupamento em Grupos Homogêneos (GHs) para ações de cobrança direcionadas.
- **Caminho:** `recuperacao_credito_veiculos/`

### 2. **Manutenção de Crédito para Veículos**
- **Descrição:** Este projeto desenvolve um modelo preditivo para manutenção de crédito em financiamentos de veículos, com foco em prever inadimplência em função de variáveis transacionais e comportamentais.
- **Tecnologias Utilizadas:** Python, pandas, LightGBM, XGBoost, Optuna.
- **Modelo Final:** LightGBM otimizado para identificar padrões de comportamento.
- **Caminho:** `manutencao_credito_veiculos/`

### 3. **Detecção de Fraude Transacional**
- **Descrição:** Identificação de atividades fraudulentas em transações financeiras, utilizando modelos supervisionados e não supervisionados. Um desafio especial foi o uso de **AutoEncoder** como abordagem alternativa para detecção de anomalias.
- **Tecnologias Utilizadas:** Python, pandas, scikit-learn, TensorFlow, AutoEncoder, Optuna.
- **Modelo Final:** Comparação entre o AutoEncoder e modelos baseados em árvores (LightGBM e XGBoost), com destaque para o AutoEncoder em detecção não supervisionada.
- **Caminho:** `deteccao_fraude_transacional/`

### 4. **Forecast de Vendas**
- **Descrição:** Criação de um modelo preditivo para prever vendas de produtos com base no histórico, utilizando tanto o LightGBM (Regressor) quanto o Prophet para comparação de desempenho.
- **Tecnologias Utilizadas:** Python, pandas, LightGBM, Prophet, Optuna.
- **Modelo Final:** LightGBM, devido ao menor erro absoluto médio (MAE) em relação ao Prophet.
- **Caminho:** `forecast_venda/`

---

## Ferramentas e Tecnologias

As ferramentas utilizadas nos projetos foram organizadas em categorias:

### Manipulação e Pré-processamento de Dados
- **pandas**: Manipulação e limpeza de dados.
- **NumPy**: Operações numéricas e vetorização.
- **scikit-learn**: Transformações e pré-processamento, como imputação e codificação de variáveis.
- **Optuna**: Otimização de hiperparâmetros.

### Modelagem e Algoritmos
- **LightGBM**, **XGBoost**, **CatBoost**: Modelos baseados em árvores de decisão para classificação e regressão.
- **scikit-learn**: Modelos clássicos como árvores de decisão e pipelines preditivos.
- **TensorFlow** e **Keras**: Construção de redes neurais, incluindo AutoEncoders.
- **Prophet**: Modelos de séries temporais para capturar tendências e sazonalidade.

### Visualização e Interpretação
- **Matplotlib** e **Seaborn**: Criação de gráficos e análise visual de dados.
- **SHAP**: Interpretação de modelos preditivos e análise de impacto das features.

### Otimização e Seleção de Variáveis
- **Optuna**: Ajuste de hiperparâmetros.
- **Forward Feature Selection**: Seleção iterativa de variáveis relevantes.

---

## Como Usar

1. **Clone o repositório:**
   ```bash
   git clone https://github.com/seu-repositorio.git

2. Navegue até a pasta do projeto desejado.

3. Cada projeto contém um arquivo README.md detalhado, explicando o contexto, os objetivos e as instruções para execução do código.

4. Certifique-se de instalar as dependências necessárias antes de executar o código.

## Autores e Contribuições

Todos os projetos deste repositório foram desenvolvidos por **Rafael Nunes de Oliveira**. Contribuições e sugestões são sempre bem-vindas!

## Licença

Este repositório não possui uma licença específica.