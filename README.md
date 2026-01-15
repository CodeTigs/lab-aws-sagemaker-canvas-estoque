# 📊 Previsão de Estoque Inteligente na AWS com [SageMaker Canvas](https://aws.amazon.com/pt/sagemaker/canvas/)

Bem-vindo ao desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas. Neste Lab DIO, você aprenderá a usar o SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML). Siga os passos abaixo para completar o desafio!

## 📋 Pré-requisitos

Antes de começar, certifique-se de ter uma conta na AWS. Se precisar de ajuda para criar sua conta, confira nosso repositório [AWS Cloud Quickstart](https://github.com/digitalinnovationone/aws-cloud-quickstart).


## 🎯 Objetivos Deste Desafio de Projeto (Lab)

![image](https://github.com/digitalinnovationone/lab-aws-sagemaker-canvas-estoque/assets/730492/72f5c21f-5562-491e-aa42-2885a3184650)

- Dê um fork neste projeto e reescreva este `README.md`. Sinta-se à vontade para detalhar todo o processo de criação do seu Modelo de ML para uma "Previsão de Estoque Inteligente".
- Para isso, siga o [passo a passo] descrito a seguir e evolua as suas habilidades em ML no-code com o Amazon SageMaker Canvas.
- Ao concluir, envie a URL do seu repositório com a solução na plataforma da DIO.


## 🚀 Passo a Passo

### 1. Selecionar Dataset

-   Navegue até a pasta `datasets` deste repositório. Esta pasta contém os datasets que você poderá escolher para treinar e testar seu modelo de ML. Sinta-se à vontade para gerar/enriquecer seus próprios datasets, quanto mais você se engajar, mais relevante esse projeto será em seu portfólio.
-   Escolha o dataset que você usará para treinar seu modelo de previsão de estoque.
-   Faça o upload do dataset no SageMaker Canvas.

### 2. Construir/Treinar

-   No SageMaker Canvas, importe o dataset que você selecionou.
-   Configure as variáveis de entrada e saída de acordo com os dados.
-   Inicie o treinamento do modelo. Isso pode levar algum tempo, dependendo do tamanho do dataset.

### 3. Analisar

-   Após o treinamento, examine as métricas de performance do modelo.
-   Verifique as principais características que influenciam as previsões.
-   Faça ajustes no modelo se necessário e re-treine até obter um desempenho satisfatório.

### 4. Prever

-   Use o modelo treinado para fazer previsões de estoque.
-   Exporte os resultados e analise as previsões geradas.
-   Documente suas conclusões e qualquer insight obtido a partir das previsões.

## 🤔 Dúvidas?

Esperamos que esta experiência tenha sido enriquecedora e que você tenha aprendido mais sobre Machine Learning aplicado a problemas reais. Se tiver alguma dúvida, não hesite em abrir uma issue neste repositório ou entrar em contato com a equipe da DIO.

# 📊 Previsão de Estoque Inteligente na AWS com SageMaker Canvas

Bem-vindo ao desafio de projeto "Previsão de Estoque Inteligente na AWS com SageMaker Canvas". Neste Lab da DIO, utilizei o Amazon SageMaker Canvas para criar previsões de estoque baseadas em Machine Learning (ML), passando por todo o ciclo de vida de um projeto de Data Science: desde a preparação dos dados até a análise de métricas de performance.

## 📋 Pré-requisitos e Ferramentas

* **Conta AWS Ativa**
* **Amazon SageMaker Canvas**: Ferramenta No-Code para construção de modelos de ML.
* **Dataset**: Histórico de estoque e vendas (disponível na pasta `datasets`).

## 🎯 Objetivos do Projeto

O objetivo principal foi desenvolver um modelo capaz de prever o comportamento do estoque de varejo, auxiliando na tomada de decisão para evitar *stockouts* (falta de produtos) ou excesso de armazenamento.

## 🚀 Passo a Passo da Implementação

### 1. Seleção e Ingestão de Dados
Naveguei até a pasta `datasets` deste repositório e escolhi o arquivo contendo histórico de vendas. O dataset foi carregado no SageMaker Canvas, onde foi feita a análise exploratória preliminar para identificar colunas críticas.

### 2. Construção e Treinamento (Build & Train)
A fase de treinamento foi configurada com as seguintes premissas:
* **Dataset Importado**: Varejo e Estoque.
* **Variável Target**: `QUANT_ESTOQUE` (O que queremos prever).
* **Identificador de Item**: `ID_PRODUTO`.
* **Carimbo de Data/Hora**: `DATA_EVENTO`.
* **Modelagem**: Time Series Forecasting (Previsão de Séries Temporais).

### 🧠 Análise e Implementações Técnicas (O Diferencial)

Durante a configuração do modelo, foram aplicadas estratégias para maximizar a precisão:

1.  **Sazonalidade e Feriados:** A coluna `Holiday_BR` foi fundamental. O modelo detectou que feriados nacionais impactam diretamente o fluxo de estoque (impacto de **~10.3%** na previsão), ajustando a curva de demanda para essas datas específicas.

2.  **Influência de Variáveis:**
    A análise de correlação mostrou que a variável `QUANT_ESTOQUE` histórica é o maior preditor (**~39.3%** de impacto), validando a consistência dos dados de entrada.
<img width="540" height="323" alt="image" src="https://github.com/user-attachments/assets/d2993343-a5f6-4504-a892-1f02e00d6167" />

3.  **Métricas de Performance Otimizadas:**
    O modelo final alcançou métricas de alta precisão, superando benchmarks tradicionais de varejo:
    * **MAPE (Mean Absolute Percentage Error): 11%**. Isso indica uma margem de erro muito baixa. Para cada 100 unidades, o modelo erra em média apenas 11.
    * **WAPE (Weighted A.P.E.): 10.7%**. O erro ponderado é ainda menor, demonstrando que o modelo é extremamente confiável em volumes altos de estoque, onde o risco financeiro é maior.
    * **MASE: 0.840**. Sendo menor que 1, comprova que o modelo de ML é matematicamente superior a uma previsão "ingênua" (média simples).
<img width="1557" height="869" alt="image" src="https://github.com/user-attachments/assets/6255dbc1-53fe-4434-8b72-d5b899c919c6" />

### 4. Previsão e Resultados (Predict)
O modelo gerou previsões probabilísticas para auxiliar na gestão de risco:
* **P10 (Cenário Pessimista):** Limite inferior de estoque recomendado.
* **P50 (Cenário Realista):** A previsão mais provável.
* **P90 (Cenário Otimista):** Limite superior para datas de alta demanda.
<img width="1766" height="685" alt="image" src="https://github.com/user-attachments/assets/6ec122e5-ec23-473c-a6be-456a65444429" />
## 📈 Conclusões

O uso do SageMaker Canvas permitiu criar um modelo robusto sem a necessidade de codificação complexa, mas com toda a inteligência estatística necessária. As métricas obtidas (especialmente o **Avg. wQL de 0.066**) demonstram que o modelo tem alta confiança em suas faixas de predição, tornando-o uma ferramenta viável para aplicação real em logística e varejo.

---
*Projeto desenvolvido como parte do Bootcamp da DIO.*




