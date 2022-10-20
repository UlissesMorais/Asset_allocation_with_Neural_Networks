# Asset Allocation with Neural Networks

Asset Allocation model created in Python, using TensorFlow and Keras.

## Table of Contents

* [Introduction](#introduction)
* [Technologies](#technologies)
* [Scope and functionalities](#scope-and-functionalities)
* [Examples of use](#examples-of-use)

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

### 1st notebook: trainpred_datasets_NNs

Como próprio nome sugere, obtêm os datasets de treinamento e predição. Como estamos tratando de séries temporais, i.e. a cotação dos fundos é diária, para obter os datasets foram definidos janelas e períodos entre 2014 e 2022 (out/2022) como segue na imagem abaixo.

![This is an image](/media/windows_table.PNG)





## Examples of use

