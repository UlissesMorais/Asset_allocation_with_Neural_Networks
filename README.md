# Asset Allocation with Artificial Neural Networks

Artificial Neural Networks model created in Python (with TensorFlow and Keras) to do asset allocation.


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

This project is a case study, aiming to develop an artificial neural network model to do asset allocation. By allocation, it is understood that given a set of financial assets (stocks, indices, investment funds, etc.) the model would predict the ideal distribution in each of them. In this project, investment funds, such as FIMs and FIAs, were used as the financial assets. Today in Brazil, approx. R$ 2.3 trillion is allocated in both asset classes combined (source: **[ANBIMA](https://www.anbima.com.br/pt_br/informar/estatisticas/fundos-de-investimento/fi-consolidado-diario.htm)**).

To perform the optimal allocation, it is necessary to define which parameter will be optimized. The most common are smaller risk, higher return, and higher return-to-risk ratio. In this project, the last was chosen.

For results validation, a backtest was carried out from 2014 to 2022. Later, these backtest results were confronted with the results obtained by **[Modern Portfolio Theory](https://en.wikipedia.org/wiki/Modern_portfolio_theory) (MPT)**, which served as a benchmark.
 
 
## Technologies

* Python 3.10
* TensorFlow 2.9
* PyPortfolioOpt v1.5.3


## Scope and functionalities

The project is divided into five notebooks:

&nbsp;&nbsp;&nbsp;**1.**  trainpred_datasets_NNs

&nbsp;&nbsp;&nbsp;**2.**  NNs_maxsharpe_model

&nbsp;&nbsp;&nbsp;**3.** performance_NNs_predicted_weights

&nbsp;&nbsp;&nbsp;**4.** performance_MKW_predicted_weights

&nbsp;&nbsp;&nbsp;**5.** boxplot_performances

Each file has a specific purpose, which will be detailed below.


### 1st notebook

As the name suggests, this notebook computes the training and prediction datasets. The price is a time series, i.e. varies daily. To build the datasets, windows and periods were defined between 2014 and 2022 (Oct/2022) as shown in the image below.

![This is an image](/media/windows_table.PNG)

The windows are composed of four periods, where three periods are for training and one for prediction. Portfolios are assembled with a set of funds imported from a pre-defined spreadsheet, which is in the "funds_spreadsheets" folder. In this project, two spreadsheets were selected with 32 funds, one of FIAs (equity funds) and another of FIMs (hedge funds).

The amount of portfolios with four funds each that can be built is 35,960. It is a sample of considerable size, which is intended to minimize possible local behaviors that do not represent the whole.

### 2nd notebook

In this notebook, the neural network architecture is assembled. Consequently, training the neural network and predicting new weights for each asset in the portfolios is also performed. The loss curves are similar to the ones below:

![This is an image](/media/loss_curve.PNG)


### 3rd notebook

In this notebook, the performances of each portfolio predicted by the neural networks are calculated. As the neural network has been optimized to search for the best risk-return ratio, the Sharpe ratio (more info about **[Sharpe ratio](https://web.stanford.edu/~wfsharpe/art/sr/sr.htm)**) is used as a performance parameter. The Neural Sharpe of each portfolio is calculated with the weights predicted by the neural network, while the Random Sharpe is calculated with randomly generated weights. In this way, the Neural Sharpe of each portfolio will be compared with a thousand Random Sharpes of the same portfolio. The performance was measured by the ratio of the number of times the Neural Sharpe is higher than the Random Sharpes, divided by a thousand.

Eg: A performance of 0.9 or 90% means that among a thousand Random Sharpes generated, the Neural Sharpe is higher than nine hundred of them.

### 4th notebook

This notebook is very similar to the previous one. The only difference is that instead of importing the neural network predicted weights, the Markowitz Sharpes (no longer the Neural Sharpes) are obtained by MPT.

### 5th notebook

In this last notebook, the performances between the results obtained by the neural network and the MPT were compared in a boxplot chart.

## Next steps

The features used in the model are the same used by MPT, which are: Returns, risks, and correlations. This gives a total of only 14 features as inputs. Some next steps to improve the model are increasing the number of features like macroeconomic variables, new correlations, and covariances. Could also change the architecture of the neural network, training hyperparameters, combined features, etc.

## Conclusion

The results obtained are quite satisfactory, using only 14 features as inputs. This shows the power of an artificial neural network and its incredible ability to find complex patterns. Setting up this project was an original idea, in order to integrate areas that I really like, such as Investments, Artificial Intelligence, Mathematics, Statistics and Programming.

Feel free to change the model and try to improve it. For more questions, just send an email to ulissesmorais27@gmail.com

