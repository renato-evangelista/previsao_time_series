# Previsão em Séries Temporais

A previsão é uma das aplicações mais comuns do aprendizado de máquina no mundo real. As empresas preveem a demanda de produtos, os governos preveem o crescimento econômico e populacional, os meteorologistas preveem o clima. A compreensão do que está por vir é uma necessidade na ciência, no governo e na indústria (sem mencionar nossas vidas pessoais!).

O objeto básico da previsão é a Série Temporal, que é um conjunto de observações registradas ao longo do tempo. Em aplicações de previsão, as observações são normalmente registradas com uma frequência regular, como diária ou mensal.

Escolhi os dados da competição “Store Sales - Time Series Forecasting”, do Kaggle¹, para realizar as previsões de vendas da rede varejista Favorita localizada no Equador. O objetivo desse projeto é criar um modelo de machine learning que prevê com mais precisão as vendas dessa rede varejista. 

# EDA

Comecei com uma análise exploratória para observar a média de vendas por loja e por produto (family).

![1](https://user-images.githubusercontent.com/90428388/231885076-205b9eeb-211f-485a-8ed5-702e1fa4dc4a.png)

Como podemos observar, grande parte das vendas deriva de “Grocery” e “Beverages”. Além disso, as lojas com a maior média de vendas são as de número “44” e “45”.

# Time-step

Time step é uma forma de analisar os dados por meio de intervalos. Nesse caso, utilizei o time dummy (conforme figura abaixo). Essa feature é responsável por contar os passos ao longo das datas e permite colocar em um gráfico as vendas da Favorita ao longo do tempo.

*img*

# Lag

Para criar uma lag feature, deslocamos as observações das vendas de um dia para o dia seguinte. Aqui, criamos um recurso de atraso de 1 etapa, embora também seja possível mudar em várias etapas.

A lag permite modelar a dependência serial. Uma série temporal tem dependência serial quando uma observação pode ser prevista a partir de observações anteriores. Podemos prever que vendas altas em um dia geralmente significam vendas altas no dia seguinte.

Você pode ver no gráfico que as vendas em um dia estão correlacionadas com as vendas do dia anterior. Quando você vê um relacionamento como esse, sabe que uma feature lag será útil.

*img*

# Trend

A Trend de uma série temporal representa uma mudança persistente e de longo prazo na média da série. A Trend é a parte de movimento mais lento de uma série, a parte que representa a maior escala de tempo de importância. Em uma série temporal de vendas de produtos, uma tendência crescente pode ser o efeito de uma expansão do mercado, à medida que mais pessoas ficam sabendo do produto ano após ano.

*img*

# Seasonality

Dizemos que uma série temporal exibe sazonalidade sempre que há uma mudança regular e periódica na média da série. As mudanças sazonais geralmente seguem o relógio e o calendário - repetições ao longo de um dia, uma semana ou um ano são comuns. A sazonalidade geralmente é impulsionada pelos ciclos naturais do mundo ao longo de dias e anos ou por convenções de comportamento social em torno de datas e horários. No caso das lojas Favorita, há um aumento das vendas nos finais de semana, conforme imagem abaixo.

**img*

# Métrica e Modelo

A métrica utilizada foi a Root Mean Squared Logarithmic Error (RMSLE). Após modelar os dados de treino com Regressão Linear, atingi uma acurácia de 0,51 nos dados de teste.

# Fontes
¹ https://www.kaggle.com/competitions/store-sales-time-series-forecasting/overview
