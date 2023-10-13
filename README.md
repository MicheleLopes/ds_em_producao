# 1- Problema de negócio
A Rossmann é uma rede de farmácia que opera mais de 3.000 drogarias em 7 países europeus. Os gerentes de loja da Rossmann solicitaram a predição de suas vendas diárias com até seis semanas de antecedência para poder tomar decisões estratégicas de futuros investimentos. As vendas das lojas são influênciadas por vários fatores, incluindo promoções, concorrentes, feriados escolares e do estado, localização, sazonalidade e sortimento de produtos.

Para realizar essa predição, a empresa disponibilizou os dados dentro da plataforma de competições de dados [Kaggle](https://www.kaggle.com/competitions/rossmann-store-sales/overview). Foram disponibilizados 1.017.209 registros das vendas realizadas de 1.115 filias da empresa, contendo 18 características únicas para cada venda realizada.

# 2- Premissas do negócio
Para a construção da solução, assumimos as seguintes premissas:
1.Realizada a previsão apenas das lojas que possuiam o valor de vendas superior a 0 na base de dados;
2.Os dias em que as lojas estavam fechadas foram descartadas da previsão.;
3.Lojas que não possuíam dados de competidores próximos tiveram o valor da distância fixada em 200.000 metros.
## 2.1- Descrição dos dados
| Atributo            | Descrição                             |
|---------------------|---------------------------------------|
| Store               | Identificador único de cada loja      |
| Date                | Data em que ocorreu o evento de venda |
| DayOfWeek           | Variável numérica que representa o dia da semana|
| Sales               | Valor de vendas do dia |
| Customers           | Quantidade de clientes na loja no dia |
| Open                | Indicador para loja aberta = 1 ou fechada = 0 |
| StateHoliday        | Indica se o dia é feriado de estado. a = Feriado público, b = Feriado de páscoa, c = Natal, 0 = Não há feriado |
| SchoolHoliday       | Indica se a loja foi ou não fechada durante o feriado escolar |
| StoreType           | Indica o modelo de lojas. Pode variar entre a, b, c, d |
| Assortment          | Indica o nível de variedade de produtos: a = básico, b = extra, c = estendido |
| CompetitionDistance	| Distância (em metros) para o competidor mais próximo |
| CompetitionOpenSince [Month/Year] | Indica o ano e mês em que o competidor mais próximo abriu |
| Promo               | Indica se a loja está com alguma promoção ativa no dia |
| Promo2              | Indica se a loja deu continuidade na promoção: 0 = loja não está participando, 1 = loja participando |
| Promo2Since [Year/Week] | Descreve o ano e semana de quando a loja começa a a promoção extendida |
| PromoInterval       | Descreve os meses em que a loja iniciou a promo2, ex.: "Feb,May,Aug,Nov" significa que a loja iniciou as promoções estendidas em cada um desses meses|
# 3- Estratégia da solução
Com o objetivo de entregar valor da maneira mais rápida possível e ajudar os gerentes na tomada de decisão, foi utilizado o método de gerenciamento cíclico CRISP-DS

Ele consiste em 9 passos ciclicos, onde a cada iteração dos nove passos, o resultado de negócio vai sendo aperfeiçoado, visando entregas cada vez mais rápidas e cada vez com mais qualidade e acertivas, possibilitando assim que as equipes que irão utilizar os resultados desenvolvidos tenham um produto um produto minimamente utilizável na primeira entrega e que é aperfeiçoado ao longo do tempo.

## 3.1- Passos do CRISP-DS:
1-**Problema de Negócio:** É nesta etapa que recebemos o problema de negócio, ou seja uma solicitação feita por alguma área ou alguém em específico;

2-**Entendimento de Negócio:** É comum recebermos direto uma solicitação de solução e não de um problema. Essa etapa tem como objetivo entender o contexto e causa raiz do problema para contruir uma solução com base na real necessidade;

3-**Coleta de Dados:** Realizar a coleta dos dados e unifica-los, buscando eles nas tabelas do(s) banco(s) de dados da empresa;

4-**Limpeza dos Dados:** Esta etapa tem como objetivo remover e tratar dados que podem atrapalhar performance final do algoritmo, como células sem valor, corrigir o tipo da variável, apagar espaços em branco, etc;

5-**Exploração dos Dados:** Analisar os dados e como eles se relacionam entre si de forma a entender os fatores que influenciam no problema apresentado, correlações e a força dessas correlações. Nessa etapa também é feita a criação e validação de hipóteses
Além da criação de novas features que serão utilizadas na etapa de Modelagem de Dados;

6-**Modelagem dos Dados:** Preparar os dados para que os algoritmos consigam aprender os padrões;

7-**Algoritmos de Machine Learning:** Esta etapa tem como objetivo selecionar e aplicar algoritmos de Machine Learning. É nesta etapa que são selecionados os algoritmos e feito a comparação de performance enetre eles, para selecionar o algoritmo que melhor performou como algoritmo final;

8-**Avaliação de Performance:** Com o algoritmo selecionado, é aplicado algum método para escolher os melhores parâmetros de acordo com a performance. Neste momento também é feito a tradução da performance do algoritmo para perfomance de negócio;

9-**Publicação da Solução:** Esta etapa tem como objetivo publicar o algoritmo selecionado, deixando publico e utilizável a solução criada. Após a publicação, podemos rodar os 9 passos novamente para aperfeiçoar a solução.

## 3.2- Produto Final
Como produto final foi entregue um Bot dentro do aplicativo Telegram que informa as previsões, facilitando assim que os gerentes possam verificar a previsão das lojas independente do local em que ele esteja. Para isso, foi criado uma API que retorna as previsões das lojas. Essa API utiliza o modelo de Machine Learning desenvolvido para realizar a previsão.
O bot do telegram pode ser acessado por [este link](t.me/rossmann_mich_bot), onde é só informar o número da loja que ele retorna com a informação da previsão para os próximos 6 meses.

## 3.3- Ferramentas Utilizadas
Para criar a solução, foram utilizadas as seguintes ferramentas:

- Linguagem de Programação Python versão 3.11.5;
- Versionador de código Git;
- Aplicação Jupyter Notebook para prototipar a solução;
- Serviço de Hospedagem em Nuvem Render;
- Técnicas de manipulação de dados utilizando a linguagem de programação Python;
- Técnicas de redução de dimensionalidade e seleção de atributos;
- Algoritmos de Machine Learning da biblioteca scikit-learn da linguagem de programação Python.


# 4- Top 3 insights de dados
A primeira etapa da análise exploratória de dados, foi realizar a construção de hipóteses para validação. Para isto, foi realizado um brainstorming e utilizado um Mindmap para ajudar nessa contruções, conforme imagem abaixo
![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/daily_store_sales.png)
Através do Mindmap, foram geradas 19 hipóteses de negócio, dentre estas 11 foram escolhidas para validação e assim, foi possível confirmar as premissas da equipe de negócios, e gerar insights para ambos.

Com as 11 hipóteses verificadas, os 3 principais insights gerados foram:

## **Insight 1- Lojas com promoções consecutivas deveriam vender mais**
**Hipótese falsa.**
Ao realizar a análise, tanto do valor de média geral, como a média ao longo do tempo (conforme o gráfico abaixo), podemos observar um comportamento em que sempre a média das lojas que aderiram apenas a primeira promoção é maior. Esse insight sugere que a aplicação da segunda promoção não tem sido tão eficaz, sendo uma oportunidade de melhoria realizar alguma mudança na implementação dessa segunda promoção ou até mesmo cancela-la.

|Promoção 1 ativa? |Promoção 2 ativa? |Média de vendas |
|------------------|------------------|----------------|
| Não              |       Não        |  R$ 6328,18    |
| Não              |       Sim        |  R$ 5529,56    |
| Sim              |       Não        |  R$ 8618,45    |
| Sim              |       Sim        |  R$ 7836,67    |

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/insight1.png)

## **Insight 2- Lojas deveriam vender mais no feriado de natal**
**Hipótese verdadeira.**
A hipotése é confirmada quando analisamos a média de vendas conforme o gráfico abaixo. Além disso, podemos identificar que a média de vendas também é bastante alta nos feriados de páscoa, o que sugere um comportamento de aumento de demanda em grandes feriados.
![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/insight2.png)

## **Insight 3- Lojas com promoções consecutivas deveriam vender mais**
**Hipótese verdadeira.**
Conforme o gráfico, A média de vendas no segundo semestre é maior, mas o aumento no segundo semestre ocorre principalmente por conta do mês de dezembro.

|Semestre    | Média       |
|------------|-------------|
| 1 semestre | R$ 6879,13  |
| 2 semestre | R$ 7065,85  |

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/insight3.png)

# 5. Modelagem dos dados

## 5.1 Preparação dos dados

O aprendizado de máquina dos algoritmos de Machine Learning é facilitado com dados númericos e na mesma escala. Por conta disso, antes da etapa de aplicação dos algoritmos foram realizadas algumas transformações nos dados.

### 5.1.1 Re-escala

Ao analisar nossas variáveis numéricas na análise exploratória de dados, nenhuma possuia uma distribuição normal, que se caracteriza por uma distribuição de probabilidade contínua, onde sua distribuição é simétrica em torno de sua média. Dessa forma foram aplicados os métodos de re-escala min-max e robust Scaler.
Para escolha do melhor método foram analisadas as variáveis individualmente através de gráficos de caixa (boxplot) e, para as que foi identificado que a presença de outliers era muito forte, foi escolhido a Robust Scaler. Com base nesse critério, os métodos de aplicação de re-escala ficaram conforme a tabela abaixo:

tabela com as variáveis numéricas e cada resscala feita

|  Variável         |  Tipo da variável  | Método      |
|-------------------|--------------------|-------------|
|competition_distance|      Numérica      |Robust Scaler|
|competition_time_month|      Numérica      |Robust Scaler|
|promo_time_week   |      Numérica      |MinMax Scaler|
|year              |      Numérica      |Minmax Scaler|


### 5.1.2 Encoding

Para as variáveis categóricas, foram aplicadas técnicas de encoding, de modo a traduzi-las de maneira numérica. Para a escolha do melhor método, foi analisado cada variável individualmente e aplicado de acordo com o que faria mais sentido para o contexto de cada variável. Dessa forma a tranformação das variáveis categóricas foi realizada da seguinte forma:

|  Variável         |  Tipo da variável  | Método         |
|-------------------|--------------------|----------------|
|state_holiday      |      Categórica    |One Hot Encoding|
|store_type         |      Categórica    |Label Encoding  |
|assortment         |      Categórica    |Ordinal Encoding|


### 5.1.3 Tranformação de natureza

A transformação de natureza foi aplicada para transformar a variável resposta mais próxima de uma normal e também a aplicada na transformação de variáveis cíclicas. Abaixo a tabela com as variáveis e o método utilizado:

|  Variável  | Tipo da variável  | Método                  |
|-------------|-------------------|------------------------|
|sales        | Variável resposta |Logarithm Transformation|
|day_of_week  | Variável cíclica  |Sine and Cosine Transformation|
|month        | Variável cíclica  |Sine and Cosine Transformation|
|day          | Variável cíclica  |Sine and Cosine Transformation|
|week_of_year | Variável cíclica  |Sine and Cosine Transformation|


## 5.2 Feature selection

Por fim, antes da etapa de aplicação dos algoritmos de Machine Learning, foi realizada a seleção das features mais importantes.
Para isso, utilizamos o método de seleção de features Boruta em conjunto com as as conclusões que tivemos durante a análise exploratória dos dados e assim selecionando um total de 22 features finais como as mais importantes e impactantes da base de dados.

# 6. Aplicação e seleção dos Modelos de Machine Learning

Inicialmente, foram treinados 5 algoritmos para teste, a fim de escolher o algoritmo com a melhor perfomance e o melhor custo de implementação. Foi optado pela simplicidade nessa etapa inicial, visto que era o primeiro ciclo do projeto e o objetivo principal era entregar uma solução que fosse mínimamente utilizável para a equipe de negócios.

Os algotitmos selecionados foram:

- Avarege Model
- Linear Regression
- Linear Regression - Lasso
- Random Forest Regressor
- XGBRegressor

É importante ressaltar que a escolha por testar um modelo de média, lineares e algoritmos de árvore, foi realizada para entender se o comportamente do fenômeno poderia ser explicado por um modelo mais simples, ou se se tratava de um modelo mais complexo, trazendo a necessidade de um algoritmo mais complexo também.
Os algoritmos foram treinados e depois realizado os testes com cada um deles, para verificar qual teria a melhor perfomance.

## 6.1. Escolha da Métrica

Para defenir qual algoritmo seria utilizado, a métrica principal para comparação da performance foi a RMSE(Root Mean Squared Error), entretanto foi mensurado também a MAE (Mean Absolut Error) e MAPE (Mean Absolute Percentage Error), por se tratar de uma métrica que tem um melhor entendimento pela equipe de negócios, visto que a MAPE representa o percentual do erro em relação ao valor médio. Os primeiros teste retornaram o seguinte resultado:

|  Nome do modelo       |  MAE    |  MAPE  |  RMSE   |
|-----------------------|---------|--------|-------- |
|Random Forest Regressor| 678.78  |  9,97% | 1012.56 |
|XGBoost Regressor      | 876.71  | 13,32% | 1248.96 |
|Average Model          | 1354.80 | 45,50% | 1835.13 |
|Linear Regression	    | 1858.11 | 28,53% | 2680.70 |
|Linear Regression-Lasso| 1891.40 | 28,93% | 2743.46 |


## 6.2. Métricas dos Algoritmos - Cross Validation

Após os testes com os algoritmos selecionados, foi utilizado a técnica de Cross Validation para validar os resultados e garantir a performance real de cada uma dos modelo utilizados. Como o problema se tratava de um série temporal, foram realizadas 5 iterações com cada moddelo, respeitando a linha do tempo no treinamento dos algoritmos.
Com o Cross Validation, obtemos os seguintes resultados:

|  Nome do modelo       | MAE AVG |  MAE STD  |MAPE AVG| MAPE STD |RMSE AVG| RMSE STD |
|-----------------------|---------|-----------|--------|----------|--------|----------|
|Random Forest Regressor| 833.23  | +/- 218.62|  12%   | +/- 0.02 |1251.74 |+/- 319.33|
|XGBoost Regressor      | 1061.07 | +/- 174.86|  15%   | +/- 0.02 |1516.22 |+/- 235.44|
|Linear Regression	    | 2032.65 | +/- 265.47|  29%   | +/- 0.01 |2901.23 |+/- 391.53|
|Linear Regression-Lasso| 2117.99 | +/- 342.74|  29%   | +/- 0.01 |3058.17 |+/- 506.07|

Para uma melhor interpretação:
AVG = Média, 
STD = Desvio padrão

## 6.3. Escolha do Modelo

Embora o algoritmo Random Forest Regressor tenha sido o algoritmo que melhor performou, foi optado pelo algoritmo XGBosst Regressor nesta etapa pelo fato de que o erro entre os dois algoritmos é pequeno e o tempo de treinamento do XGBoost Regressor é mais rápido se comparado ao algoritmo Random Fores Regressor além de ocupar menos espaço de memória que o algoritmo Random Forest Regressor, deixando assim o uso de servidores em nuvem mais baratos.

## 6.4. Ajuste de Hiperparâmetros

Com a escolha do algoritmo, seguimos para etapa de ajuste dos hiperparâmetros. Novamente pensando no ganho de velocidade, utilizamos a técnica de Random Search para a busca pelo os melhores hiperparâmetros. Após 5 iterações rodando com alguns parâmetros escolhidos aleatoriamente, chegamos aos seguintes parâmetros e performance final:

Os parâmetros finais para o algoritmo XGboost foram:

|Nome parâmetro   |  Valor  |
|-----------------|---------|
|n_estimators     | 1500    |
|eta              | 0.03    |
|max_depth        | 9       |
|subsample        | 0.7     |
|colsample_bytree |  0.3    |
|min_child_weight |  8      |

Tabela com a performance do modelo final:

| Nome do modelo    |  MAE    |  MAPE  |  RMSE   |
|-------------------|---------|--------|-------- |
| XGBoost Regressor | 723.28  | 10,64% | 1043.60 |

# 7. Tradução e interpretação do erro

O modelo selecionado obteve uma performance aceitável, visto que conseguiu entender e reproduzir o padrão de vendas ao longo dos anos estudados com um erro médio absoluto de 10,64% (MAPE).
Dessa forma, as duas próximas sessões irão traduzir esse erro e os resultados do algoritmo, um do ponto de vista de negócios e outro do ponto de vista técnico da ciência de dados.
1354.80 | 45,50% | 1835.13
## 7.1 Business Performance

Com os resultados do algoritmo, conseguimos realizar a previsão de vendas para as próximas 6 semanas, para cada loja individualmente e também a margem do erro, o que nos possibilita trazer além da previsão, o pior e melhor cenário e o % do erro das previsões, auxiliando na tomada de decisão com relação a qual cenário é mais assertivo o gerente considerar.
Além disso, se levarmos em consideração que anteriormente era utilizado para previsão um modelo de média, conforme o erro no item 6.1 temos uma diferença na assertividade de R$ 631,52 o que representa uma melhoria de 47% (métrica MAE) e uma melhoria no percentual do erro absoluto médio de 35% (métrica MAPE).

Abaixo temos uma tabela com as previsões individuais das 5 lojas com a melhor performance na predição e as 5 com a pior performance. Na sequência um gráfico com a distribuição das lojas e seu erro MAPE , onde é possível observar que a maioria das lojas tem seu erro em torno do valor de 10% e temos 2 lojas com o erro bem distante dessa média, com valores acima de 50%.

| Loja |   Previsão   | Pior cenário |Melhor cenário| MAE       | MAPE  |Ranking MAPE|
|------|--------------|--------------|--------------|-----------|-------|------------|
| 259  | R$ 546.924,44| R$ 546.383,89|R$ 547.464,99 |R$ 540,55  | 4,34% | 1°         |
| 1097 | R$ 466.624,53| R$ 466.152,15|R$ 467.096,91 |R$ 472,38  | 4,47% | 2°         |
| 733  | R$ 633.979,87| R$ 633.298,73|R$ 634.661,02 |R$ 681,14  | 4,63% | 3°         |
| 1089 | R$ 365.315,31| R$ 364.713,64|R$ 365.916,98 |R$ 601,67  | 5,42% | 4°         |
| 676  | R$ 389.753,72| R$ 389.199,43|R$ 390.308,01 |R$ 554.29  | 5,54% | 5°         |
| 292  | R$ 110.098,54| R$ 106.676,31|R$ 113.520,77 |R$ 3.422,23|62,52% | 1111°      |
| 909  | R$ 227.353,34| R$ 219.495,42|R$ 235.211,27 |R$ 7.857,92|52,35% | 1112°      |
| 876  | R$ 195.054,94| R$ 190.988,87|R$ 199.121,00 |R$ 4.066,06|32,64% | 1113°      |
| 170  | R$ 190.106,06| R$ 189.042,98|R$ 191.169,14 |R$ 1.063,08|26,87% | 1114°      |
| 970  | R$ 120.569,17| R$ 120.003,15|R$ 121.135,19 |R$ 566.02  |25,53% | 1115°      |

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/mapelojas.png)

Para uma tomada de decisão mais macro, segue também o valor total das previsões:

| Previsão       |  Pior cenário  | Melhor cenário |
|----------------|----------------|----------------|
|R$282.785.952,00| 281.975.478,53 |R$283.596.417,20| 

## 7.2 Machine Learning Performance

Para avaliar a performance com aos olhos do lado técnico, a principal métrica foi a RMSE. Além disso, conforme o gráfico abaixo, conseguimos comparar as vendas reais com a nossa previsão, onde de uma forma geral o modelo conseguiu reproduzir o padrão de vendas ao longo do tempo, o que confirma a qualidade do nosso modelo:

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/graficoml1.png)

E ao olhar a distribuição dos erros nos 2 gráficos abaixo, podemos observar uma distribuição normal a cerca das previsões, o que nos inidica um bom resultado do modelo selecionado.

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/graficoml2.png)

![](https://github.com/MicheleLopes/ds_em_producao/blob/main/img/graficoml3.png)

# 8. Conclusões
Conforme pôde ser verificado, o projeto resolveu o problema inicial, que era a previsão de faturamento das lojas feitas de forma manual por seus gerentes.

Outro ponto importante de destacar é que com a solução criada, os gerentes podem agora consultar através do celular a previsão das lojas de forma automática com o BOT criado, um ponte que consegue trazer de forma simples o produto criado pelo cientista de dados para uma pessoa da área de negócios, agregando valor e agilidade na tomada de decisão.

# 9. Lições Aprendidas

- Priorizar tarefas e soluções;
- Desenvolver soluções de forma cíclica, entregando assim resultado mais rapidamente;
- Construção de um BOT para o aplicativo de mensagens Telegram, afim de agilizar o acesso à informações.

# 10. Próximos Passos

- Investigar a razão de algumas lojas estarem com previsões ruins e avaliar a possibilidade  modelos específicos para a previsão dessas lojas;
- Selecionar outros algoritmos para treinamento no próximo ciclo, a fim de buscar uma solução que melhore o desempenho da previsão;
- Criar uma aplicação Web utilizando o framework Streamlit para dar acesso Web às previsões para os gerentes das lojas;
- Criar novas Features para tentar melhorar a perfomance do modelo atual e de modelos futuros.
