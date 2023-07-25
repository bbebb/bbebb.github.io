# Brendan Bebb
### University of Michigan, B.S. Data Science
#### Baseball Analyst, Michigan Sports Analytics Society
#### Treasurer, Captain, Michigan Club Baseball

[LinkedIn](www.linkedin.com/in/brendanbebb)


[LeetCode](https://leetcode.com/brendanbebb/)

# Projects

## [Project 1: Stock Market Trend Predictor](https://github.com/bbebb/stock-market-trend-predictor/tree/main)
### Overview
This project works to recreate and improve the accuracy of a stock market trend predictor proposed in a [dissertation](https://etd.auburn.edu/bitstream/handle/10415/5652/Application%20of%20machine%20learning%20techniques%20for%20stock%20market%20prediction.pdf?sequence=2&isAllowed=y) proposed by Bin Weng of Auburn University. 
The program serves to predict future movement of the stock market using historical data using various fitted formulas:
  
<img width="394" alt="Screen Shot 2023-07-25 at 12 26 20 PM" src="https://github.com/bbebb/bbebb.github.io/assets/73957927/a697d756-4bd9-45e8-8f15-a0bfcb551934">
  
### Recreating Support Vector Models
The first half of this project works to recreate Weng's support vector models using historical Apple, Inc. (AAPL) stock data [(csv)](https://github.com/bbebb/stock-market-trend-predictor/blob/main/AAPL.csv) obtained from Yahoo.com. Upon splitting the data into training and testing files, the training data was used to predict the responses for the formula when the model was given the testing data.  
  
**The recreation of Target 3 was the most accurate model, having an accuracy of 83.1%.** It is feesible that this model was the most accurate, as it is the most naive of the models: when comparing Day 2 to Day 1, the value of the stock either went up or down. Since the most simple SVM model produces the most accurate predictions, the second half of this project works to improve the accuracy of these models using Adaptive Boosting trees.  

### Improving with Adaptive Boost Trees
To improve the model accuracy, an adaptive boosting algorithm using gradient boosting machines for each target was implemented. An example of the fitted AdaBoost tree model is as follows:
  
```{r}
# Target 1
boost.t1 = gbm(t1 ~ t2 + t3 + t4 + t5, data = trainApple6,
    distribution = "gaussian", n.trees = 1000,
    interaction.depth = 4)
```
  
This formula combines the five targets, with one being the response, and the other 5 targets being the predictors. Each model seeks to identify the optimal number of trees neeeded to obtain the least amount of test error (thus maximizing the accuracy).

<img alt="Screen Shot 2023-07-25 at 12 11 59 PM" src="https://github.com/bbebb/bbebb.github.io/assets/73957927/a0302349-fc0c-4a14-ac0d-f92f53a9d318" width="350" height="200"/>
  
As illustrated in the graph above, the lowest misclassification rate obtained was 11.87% for Target 4, meaning **the most accurate model was 88.13% accurate.** While Adaptive Boosting trees improved stock market trend prediction, the difference is near negligible. 

## [Project 2: Major League Baseball Player Analysis](https://github.com/bbebb/msas-baseball-trends)


