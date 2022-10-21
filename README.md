# Asset Allocation with Neural Networks

Asset Allocation model created in Python, using TensorFlow and Keras.


## Table of Contents

* [Introduction](#introduction)
* [Technologies](#technologies)
* [Scope and functionalities](#scope-and-functionalities)
    * [1st notebook](#1st-notebook)
    * [2nd notebook](#2nd-notebook)
    * [3rd notebook](#3rd-notebook)
    * [4th notebook](#4th-notebook)
    * [5th notebook](#5th-notebook)
* [Next steps](#next-steps)
* [Conclusion](#conclusion)


## Introduction

Este projeto teve como objetivo fazer um estudo de caso, desenvolvendo um modelo de rede neural para fazer alocação de ativos financeiros. Por alocação, entende-se que dado um conjunto de ativos financeiros (ações, índices, fundos de investimento etc.) o modelo preveria qual a distribuição de capital ideal em cada um deles. Neste projeto, foram utilizados fundos de investimento (FIMs e FIAs) como ativos financeiros, visto que hoje no Brasil estão alocados ~ R$ 2.3 trilhões em ambas as classes de ativos somadas (fonte: **[ANBIMA](https://www.anbima.com.br/pt_br/informar/estatisticas/fundos-de-investimento/fi-consolidado-diario.htm)**).

Para realizar a alocação ideal, é preciso definir qual parâmetro será otimizado. Por exemplo: Gostaríamos de ter um portfolio com menor risco? Maior retorno? Melhor relação risco-retorno? Neste projeto, optou-se pelo melhor **risco-retorno**.

Para validação final dos resultados, foi feito um backtest de 2014 a 2022 e posteriormente confrontados com resultados obtidos pelo modelo **[Modern portfolio theory](https://en.wikipedia.org/wiki/Modern_portfolio_theory)**.
 
 
## Technologies

* Python 3.10
* TensorFlow 2.9
* PyPortfolioOpt v1.5.3


## Scope and functionalities

O projeto está dividido em cinco notebooks:

&nbsp;&nbsp;&nbsp;**1.**  trainpred_datasets_NNs

&nbsp;&nbsp;&nbsp;**2.**  NNs_maxsharpe_model

&nbsp;&nbsp;&nbsp;**3.** performance_NNs_predicted_weights

&nbsp;&nbsp;&nbsp;**4.** performance_MKW_predicted_weights

&nbsp;&nbsp;&nbsp;**5.** boxplot_performances

Cada arquivo tem uma finalidade específica, que serão detalhados mais a seguir.


### 1st notebook

Como próprio nome sugere, obtêm os datasets de treinamento e predição. Como estamos tratando de séries temporais, i.e. a cotação dos fundos é diária, para obter os datasets foram definidos janelas e períodos entre 2014 e 2022 (out/2022) como segue na imagem abaixo.

![This is an image](/media/windows_table.PNG)

As janelas de análise são compostas de quatro períodos, em que três períodos são para treinamento e um para predição. Os portfolios são montados com um conjunto de fundos importados de uma planilha pré definida, que está na pasta "planilha_fundos". Neste projeto foram selecionados duas tabelas com 32 fundos cada, uma de FIAs (fundos de investimento de ações) e outra de FIMs (fundos de investimentos multimercado).

O total de portfolios que podem ser montados para cada tabela é de 35.960, visto que cada portfolio contêm 4 fundos. Por ser uma amostra de tamanho considerável, pretende-se minimizar possíveis comportamentos pontuais que não representem o todo.

### 2nd notebook

Neste arquivo é montada a arquitetura da rede neural, além do treinamento e predição final de novos pesos de cada ativo do portfolio. As curvas de perda são similares às abaixo:

![This is an image](/media/loss_curve.png)


### 3rd notebook

São calculadas as performances de cada portfolio previstos pela rede neural. Como a rede neural foi otimizada para buscar a melhor relação risco-retorno, é utilizado o Sharpe ratio (sobre [Sharpe ratio](https://web.stanford.edu/~wfsharpe/art/sr/sr.htm)) como parâmetro de performance. O Sharpe Neural de cada portfolio é calculado com os pesos previstos pela rede neural, enquanto o Sharpe Aleatório é calculado com pesos gerados de forma aleatória. Desta forma, o Sharpe Neural de cada portfolio será comparado com mil Sharpes Aleatórios deste mesmo portfolio, sendo a performance medida pela razão do número de vezes em que o Sharpe Neural é maior do que o Sharpes Aleatórios, divido por mil.

Ex.: Uma performance de 0.9 ou 90% significa que dentre mil Sharpes Aleatórios gerados, o Sharpe Neural é maior do que novecentos destes.

### 4th notebook

Este notebook é bem similar ao anterior, a única diferença é que ao invés de importar os pesos da rede neural, os Sharpes Markowitz (não mais os Sharpes Neurais) são obtidos pela Teoria Moderna de Portfolio.

### 5th notebook

Neste último notebook, são comparadas as performances entre os resultados obtidos pela rede neural e pela MPT. São gerados gráficos de Boxplot como o abaixo:


![This is an image](/media/boxplot.PNG)


## Next steps



## Conclusion


