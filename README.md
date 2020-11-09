# PREVISÃO AUTOMÁTICA, COM REDES NEURAIS, DA PROBABILIDADE POR BAIRROS DE SEREM SOLICITADOS TRANSPORTES POR APLICATIVOS

Monografia apresentada ao Departamento de Engenharia Elétrica da PUC/Rio como parte dos requisitos para a obtenção do título de Especialização em Business Intelligence

Data: 31/08/2020

## Autor: Fernando Mauro **Buleo** Barbosa

### O texto abaixo apresenta um resumo do trabalho. Clique no link a seguir para acessar a [Monografia Completa](https://github.com/buleo/TCCTeste/blob/main/BI-Master-Monografia-final%20-FMBB.pdf).

## RESUMO
No presente trabalho foi desenvolvido modelo preditivo visando identificar as áreas de cidades com maior probabilidade de demandarem transporte por aplicativo, a cada dia e hora. O modelo preditivo foi desenvolvido em uma rede neural e treinado para prever a probabilidade de transportes serem demandados em 3 (três) cidades brasileiras. Para o treinamento foi utilizada a base completa de 1 (um) mês de 2020 de transportes realizados por aplicativo. 

Os melhores resultados obtidos indicaram que, em 84% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transporte com uma distância de até 3 posições em relação a ordem (“ranking”) real de bairros, quando consideramos os 5 que mais demandam transportes. Expandindo a análise para os 10 bairros que mais solicitam transportes, foi verificado que, em 77% dos casos, o modelo consegue prever a probabilidade de bairros demandarem transportes com uma distância de até 3 posições em relação ao “ranking” real.


## ABSTRACT
In this work, a predictive model was developed to identify the areas of cities most likely to require transportation, every day and hour. The predictive model was developed in a neural network and trained to predict the likelihood of a demand for transport in 3 (three) Brazilian cities. For the training of the model, the complete base of transports performed in 1 (one) month of the year 2020 of a transport application was used.

The best results obtained indicated that, in 84% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking", when we consider the 5 neighborhoods that most originate races. Expanding the analysis to the 10 neighborhoods that demand the most transport, It was found that, in 77% of the cases, the model is able to predict the probability of neighborhoods requiring transport with a distance of up to 3 positions in relation to the real "ranking".

## OBJETIVOS DO TRABALHO
Para realização desse trabalho foi obtida, junto a empresa [Gaudium](https://gaudium.global/), a qual desenvolveu e comercializa o aplicativo de transportes [Machine](https://machine.global/), a base completa de transportes realizados em janeiro de 2020. Essa base dispõe para cada transporte, de informações como a data da “corrida” (transporte), horário, cidade de partida, cidade de destino, bairro de partida e bairro de destino. De posse dessa base os objetivos do trabalho foram: 
  -	Gerar base de informações, a partir da base disponível de transportes realizados, com a probabilidade de cada bairro, em cada cidade de partida, demandar transportes a cada dia e hora do mês de modo a servir como base de treino e base de testes do modelo preditivo a desenvolver
  -	Eleger, dentre as 1.118 cidades de partida presentes na base, quais seriam usadas nesse estudo
  -	Desenvolver Rede Neural para prever, por método de regressão, a probabilidade de cada bairro das cidades eleitas no estudo, demandar transportes a cada dia, de hora em hora
  
## OPORTUNIDADE E BENEFÍCIOS 

O uso da tecnologia e de métodos “inteligentes” tem sido fundamental para viabilizar o negócio de transporte por aplicativos, permitindo, inclusive, que motoristas sem experiência prévia em transportes atuem na área. Aplicativos de navegação permitem que um motorista busque um passageiro e o leve até o destino sem nunca ter ido antes aos endereços de partida e de destino. Mesmo motoristas experientes no ramo de transporte e conhecedores dos mapas e ruas da cidade onde atuam, podem se beneficiar dessa inteligência usando a rota mais rápida apontada pelo aplicativo naquele momento, em vez de se basearem unicamente em sua experiência prévia, insuficiente para prever situações excepcionais como congestionamentos do tráfego, sinistros nas vias etc. 

Nesse sentido, motoristas buscam circular nas áreas que, segundo a experiência adquirida, tem mais probabilidade de demandar transportes, a fim de maximizar sua receita e evitar ficarem circulando pela cidade a esmo consumindo combustível. 

O modelo proposto nesse Trabalho de Conclusão de Curso se destina a estimar, para um conjunto de cidades eleitas, a probabilidade de serem demandados transportes em cada bairro dessas cidades, a cada período de 1 (uma) hora do dia. 

Esse modelo viabiliza que qualquer motorista tenha conhecimento das áreas da cidade com maior probabilidade de originar transportes naquele dia e horário, independente de experiência prévia. Dessa forma, ele poderá se dirigir para uma das áreas apontadas por essa solução, que se situe mais próxima de sua localização atual. 
Alguns dos benefícios dessa solução são:
  - Maximizar a receita dos transportadores
  -	Minimizar o custo dos transportadores, que podem despriorizar a circulação em áreas com menor probabilidade de demandar transportes, reduzindo o gasto de combustível sem receita associada
  -	Maximizar o total de clientes satisfeitos, reduzindo o tempo de espera por um transportador em função da maior disponibilidade de transportadores nas áreas que mais geram transportes

## ETAPAS DO TRABALHO
O execução desse trabalho envolveu as seguintes etapas:
  - O estudo de ferramentas de ETL
  -	O estudo de técnicas de Data Mining
  -	O estudo de modelos de Machine Learning e redes neurais para previsão por regressão
  -	O desenvolvimento de ETL para extração e transformação da base de dados do cliente em uma base de informações das probabilidades dos bairros originarem transportes
  -	Desenvolvimento de Rede Neural para previsão por regressão da probabilidade de bairros originarem transportes
  -	Execução de simulações para parametrização da Rede Neural
  -	Avaliação dos Resultados


## SOLUÇÃO - O MODELO DE INFERÊNCIA

A base histórica com as informações de um mês de transportes foi carregada e convertida, utilizando o [Pentaho](https://g.co/kgs/3B2LN7) como ferramenta de ETL, em arquivos em formato CSV (Comma Separated Values) contendo a probabilidade de cada bairro demandar corridas a cada dia e hora do mês de Janeiro/2020. Foi gerado um [arquivo para a cidade de Fortaleza](https://github.com/buleo/TCCTeste/blob/main/Corridas_Fortaleza-FINAL-Acentuado-Probabilidades-ComSemanaTeste.csv) e um [arquivo para as demais cidades](https://github.com/buleo/TCCTeste/blob/main/Corridas_Cidades_Eleitas-FINAL-Acentuado-Probabilidades-ComSemanaTeste.csv) eleitas para estudo nesse trabalho. Esses arquivos serviram como base de treino e base de testes do modelo preditivo.

A fim de garantir que, tanto a base de treino como a base de testes dispusesse de registros de todas as horas e todos os dias da semana, foram considerados para teste os transportes ocorridos no período de 12 a 18 de janeiro de 2020 e para treino os demais dias.

O modelo de inferência foi desenvolvido em um programa utilizando a linguagem [Python](https://www.python.org/). 

Para criação da rede neural foi utilizada a biblioteca [Keras](https://keras.io/) do Python.
Foi utilizada uma rede neural de 3 camadas.
Como função de ativação dos neurônios da rede foi utilizada a função “Relu”.

Foi utilizado o [Google Colaboratory](https://colab.research.google.com/notebooks/intro.ipynb) para executar as simulações do modelo. 

Vários otimizadores foram utilizados nas simulações sendo que os melhores resultados foram obtidos com os listados abaixo:
  - SGD - Otimizador de Gradiente descendente com Momentum   
  - NAdam - Otimizador que implementa o algoritmo Adam conjugado com o momentum Nesterov

Clique [aqui](https://github.com/buleo/TCCTeste/blob/main/TCC_Gaudium_SemanaTeste_Limpo.ipynb) para acessar o código completo do programa em [Jupiter Notebook](https://jupyter.org/). 


## SIMULAÇÕES

Foram realizadas, ao todo, 127 simulações desse modelo. Os parâmetros cuja configuração foi variada nessas simulações são os seguintes:

- Número de Camadas da Rede Neural

   Do total de 127 simulações, 116 foram realizadas com redes neurais de 3 camadas. Após atingir o melhor modelo com 3 camadas, algumas simulações foram realizadas com 4 ou 5 camadas (11 simulações no total). Os resultados não apresentaram ganhos significativos, portanto as melhores soluções mantiveram somente 3 camadas.
   
-	Quantidade de Neurônios das Camadas Escondidas

   As simulações, em geral, seguiram a heurística mencionada na seção 3.3.4 da [monografia](https://github.com/buleo/TCCTeste/blob/main/BI-Master-Monografia-final%20-FMBB.pdf) quanto a quantidade de neurônios das camadas escondidas.
   
-	Otimizador

   Foram realizadas simulações utilizando os otimizadores _[SGD](https://keras.io/api/optimizers/sgd/), [RMSPROP](https://keras.io/api/optimizers/rmsprop/), [Adam](https://keras.io/api/optimizers/adam/), [Nadam](https://keras.io/api/optimizers/nadam/), [Adamax](https://keras.io/api/optimizers/adamax/), [Adagrad](https://keras.io/api/optimizers/adagrad/) e [Adadelta](https://keras.io/api/optimizers/adadelta/)_. Os melhores resultados, contudo, foram obtidos com os otimizadores _**Nadam e SGD**_.
   
-	Indicador de Perda

   Foram realizadas simulações utilizando os indicadores MAE, MSE e MAPE, associados ao algoritmo otimizador. Observou-se, contudo, que a maior parte dos valores a serem previstos eram muito pequenos. Considerando as bases de informações das cidades eleitas, 88% dos registros (bairros por horário) apresentavam probabilidade inferior a 5% (0,05). 
  
   Assim, os erros medidos pelos indicadores MAE e MSE eram muito pequenos, levando a resultados menos satisfatórios quando esses foram utilizados no modelo preditivo.
Já o indicador MAPE, por representar a distância percentual entre o valor previsto e o real, mede gera valores mais significativos proporcionando melhores resultados para esse conjunto de simulações. 

-	Épocas de Treinamento

   Foram realizadas simulações com até 20.000 épocas de treinamento. No entanto, o ajuste desse parâmetro evidenciou que bastavam em torno de 250 épocas para obter os melhores resultados. 
   
   A realização de simulações com até 20.000 épocas proporcionou a observação do fenômeno de Overfitting (Super Treinamento), conforme podemos observar no gráfico abaixo. Tal gráfico representa a variação do indicador MAE em função do total de Épocas utilizadas na simulação. Nas simulações ilustradas nesse gráfico foi utilizada rede neural de 3 camadas com 160, 80 e 1 neurônio respectivamente. O otimizador utilizado foi o Adam. A cidade em questão foi Petrolina.
   
   ![Overfit](https://github.com/buleo/TCCTeste/blob/main/Overfit-Gr%C3%A1fico.png "Overfit em rede neural de 3 camadas com 160, 80 e 1 neurônios e Otimizador Adam")

-	Faixa Horária
   
   Na base de informações disponibilizada de transportes realizados, para as cidades eleitas nesse trabalho, 73% dos transportes ocorriam no período de 8 as 19 horas.  Por conta disso, foram executadas não só simulações visando desenvolver modelos para prever a probabilidade de transportes a qualquer hora do dia, mas também simulações visando prever somente os transportes no período de 8 às 19 horas, faixa próxima ao “Horário Comercial”.

   O objetivo foi otimizar os resultados dos modelos nesse período horário (próximo ao “Horário Comercial”), sem prejuízo da relevância dos resultados dado que esse período corresponde a 73% dos transportes. 

   A figura abaixo apresenta a distribuição do total de transportes realizados por hora para cada uma das cidades eleitas.

   ![FaixaHoraria](https://github.com/buleo/TCCTeste/blob/main/FaixaHoraria-Gr%C3%A1fico.png "Distribuição do total de transportes realizados por hora para cada uma das cidades eleitas")


## RESULTADOS

Foram realizadas simulações para as cidades de Fortaleza, Patos de Minas e Petrolina. Os melhores resultados foram obtidos para Fortaleza e estão sumarizados nessa seção. A relação completa de resultados de Fortaleza, bem como, os resultados das demais cidades pode ser obtida diretamente na [monografia](https://github.com/buleo/TCCTeste/blob/main/BI-Master-Monografia-final%20-FMBB.pdf)

### Fortaleza - Melhores Resultados

A tabela abaixo apresenta os parâmetros da simulação na qual foram obtidos os melhores resultados utilizando o Otimizador Nadam, na cidade de Fortaleza, considerando transportes iniciados em qualquer hora do dia. Apresenta, também, os resultados dos indicadores de performance obtidos nessa simulação. 

| Nome do Parâmetro | Valor |
| --- | --- |
| Faixa Horária | 0 a 23 horas |
| Algoritmo Otimizador | Nadam |
| Parâmetros do Algoritmo Otimizador	| Default 	|
| Rede Neural	| 3 camadas densamente conectadas com 314, 157 e 1 neurônio respectivamente |
| Total de Épocas | 10 |
| Indicador de Perda | MAPE |
| Resultados	| RMSE:		1,6736 |
| | MSE:		2,8009 |
| | MAE:		0,797523916 |
| | MAPE:		31,68181038 |

O gráfico abaixo apresenta, para cada elemento da base de teste, a distância entre a probabilidade real e a estimada pelo modelo nessa simulação. 






