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

### Métricas da aba Analyze

<img width="1557" height="869" alt="image" src="https://github.com/user-attachments/assets/6255dbc1-53fe-4434-8b72-d5b899c919c6" />

### O que significam:
- MAPE (Mean Absolute Percentage Error) de 11% = Excelente. O erro médio absoluto é de apenas 11%. Se o estoque real for 100 unidades, o modelo prevê algo entre 89 e 111. Para varejo e estoque, um MAPE abaixo de 15-20% já é considerado muito bom.
- WAPE (Weighted A.P.E.) de 10.7% = O erro ponderado é ainda menor que o MAPE. Isso indica que o modelo acerta ainda mais quando os volumes de estoque são altos (onde o erro custaria mais caro) e talvez erre um pouco mais nos volumes baixos, o que é o comportamento ideal.
- Avg. wQL (Weighted Quantile Loss) de 0.066 = Impressionante. Quanto mais próximo de zero, melhor. Um valor de 0.066 indica que o modelo tem altíssima confiança nas faixas de probabilidade (P10, P50, P90). Ele não está "chutando" valores aleatórios; ele tem certeza da zona onde o valor cairá.
- RMSE (Root Mean Square Error) de 1.666 = O erro padrão é de aproximadamente 1,6 unidades de estoque. Dependendo da escala do seu produto (se você vende centenas por dia), errar por 1 ou 2 unidades é virtualmente irrelevante. É uma precisão cirúrgica.
- MASE (Mean Absolute Scaled Error) de 0.840 = O selo de qualidade. Como o valor é menor que 1.0, isso prova matematicamente que o seu modelo de Machine Learning é melhor do que uma "previsão ingênua" (apenas repetir o valor de ontem). O ML está agregando valor real.

### Olhando o impacto das colunas
O que é mais importante" para o modelo matemático que ele criou...

- 1. O Grande Motor: QUANT_ESTOQUE (39.37%)
Esta variável tem um impacto massivo, respondendo por quase 40% da "inteligência" da previsão.
O que significa: O modelo encontrou uma correlação fortíssima entre a quantidade de estoque que você tem disponível e o quanto você vende.
- 2. O Fator Sazonal: Holiday_BR (10.34%)
Os feriados brasileiros têm um peso relevante (~10%), mas são secundários em relação ao estoque.
O que significa: O modelo aprendeu que em dias marcados como "Feriado", o comportamento de compra muda (para melhor ou pior, dependendo do seu ramo).

<img width="540" height="323" alt="image" src="https://github.com/user-attachments/assets/d2993343-a5f6-4504-a892-1f02e00d6167" />

### Simgle Prediction
- P10 = Pessimista
- p50 = Balanceado
- p90 = Otimista
<img width="1766" height="685" alt="image" src="https://github.com/user-attachments/assets/6ec122e5-ec23-473c-a6be-456a65444429" />




