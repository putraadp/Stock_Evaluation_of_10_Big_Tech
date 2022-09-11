![image](cover.jpg)
# Risk and Return on Investment in The 10 Biggest Tech Companies in The World & Predictions for The Future

## Overview
- Evaluate the risk and return of 10 stocks of The World's Biggest Technology Companies 5 years ago to date based on annual Sharpe Ratios.
- Create a tool that functions to provide stock price predictions from companies that have the highest annual sharpe ratio evaluation results in previous evaluations.
- Machine learning with LSTM (Long Short Term Memory) model is used to predict stock prices.
- All datasets are provided from Yahoo! Finance's API. So, each daily runtime will provide the latest evaluation and prediction results.
- All graph in interactive for better visualization dan analyst experience.

## Code and Resources Used
**Python Version:** 3.10.3  
**Packages:** numpy, pandas, tensorflow, matplotlib, yfinance, plotly, cufflinks, sklearn, keras, datetime    
**Dataset source:** Yahoo! Finance's API

## Notebook Interactive View
https://nbviewer.org/github/Underscore48/Stock_Evaluation_of_10_Big_Tech/blob/main/stock.ipynb

## Collecting Data
First thing to do is to determine the 10 largest technology companies in the world, here I get a list from the [Companiesmarketcap website](https://companiesmarketcap.com/tech/largest-tech-companies-by-market-cap/) (accessed on 5 september 2022), The world's top 10 technology companies are :
- Apple (USA)
- Microsoft (USA)
- Google (USA)
- Amazon (USA)
- Tesla (USA)
- Meta Platforms (USA)
- Taiwan Semiconductor Manufacturing Company (Taiwan)
- Tencent (China)
- Nvidia (USA)
- Alibaba (China)   

For comparison, the S&P 500 is used as a benchmark here.    
Then, the stock price dataset is taken from **Yahoo! Finance's API** via the yfinance package, here we will use stock prices from the *past 5 years*.

<h3 align="center">Visualized into a graph</h3>   

![newplot0](https://user-images.githubusercontent.com/98052588/189549006-a5e9d980-88f3-4ee9-8e73-96d83e01be1f.png)
![newplot](https://user-images.githubusercontent.com/98052588/189548874-524a9d82-b7b4-4e58-93a0-b9edef8b713c.png)

## Sharpe Ratio
<p align="center">Annual Sharpe Ratio</p>   

![newplot6](https://user-images.githubusercontent.com/98052588/189549139-8475061c-8c49-44ba-9e4b-4cbade740c22.png)

Here, we can see **Microsoft, Apple, and Tesla** have the highest annual sharpe ratio from the past 5 years data stock price.   
So, if you want to buy some chips in the world's technology Companies. The 3 Companies are the best choices based on the theory put forward by Professor William F. Sharpe.

## Build Stock Price Machine Learning Model    
Because Microsoft has the highest sharpe ratio, it will be interesting if we can predict the stock price of Microsoft in the future. So, here I will create a machine learning model to predict stock prices from Microsoft.    
Here stock price of Microsoft from 5 years later. *For interactive graph can be seen on this [link](https://nbviewer.org/github/Underscore48/Stock_Evaluation_of_10_Big_Tech/blob/main/stock.ipynb)*      

![newplot7](https://user-images.githubusercontent.com/98052588/189549546-9745a949-1ab9-47d6-93f4-70b34ef696cf.png)

In this Model, I use machine learning regression model from Keras and TensorFlow for create Neural Network layers of Sequential with 2 LSTM (Long Short Term Memory) Layer and 2 Dense Layer.    
Here the summary of model :
| Layer (type)     | Output Shape    | Param # |
| ---------------- | --------------- | --------|
| lstm_10 (LSTM)   | (None, 60, 128) |   66560 |
| lstm_11 (LSTM)   | (None, 64)      |   49408 |
| dense_10 (Dense) | (None, 25)      |    1625 |
| dense_11 (Dense) | (None, 1)       |      26 |

For each 1 prediction, using 60 stock prices from 60 active market days, or basically 2 months data stock price is for 1 predictions stock price.
To get high prediction accuracy, model machine learning is trained using 1 batch data with 10 epoch. For 5 years dataset, it takes 5 minutes to complete tha training with loss around 0.0004, which is very nice.

## Result
### Prediction Price on 5 years Stock price
![newplot8](https://user-images.githubusercontent.com/98052588/189550301-b757d054-ae3b-437e-b7ef-182c92ddd976.png)
Zoom for better visualization:
![newplot9](https://user-images.githubusercontent.com/98052588/189550330-a5631c30-086c-415d-83ab-7e8c2e33ad10.png)

Here we can see the predictions and the actual stock price is very close. Here the table result:
| Accuration | MAE    | MSE   |
| ---------- | ------ | ----- |
| 99,3 %     | 0.858  | 1.322 |
