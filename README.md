# Brendan Bebb
--------------
### University of Michigan, B.S. Data Science
#### Baseball Analyst, Michigan Sports Analytics Society
#### Treasurer, Captain, Michigan Club Baseball
---------------
Hello! My name is Brendan Bebb, and I am seeking Data Analyst positions with heightened interest in Sports Analytics having graduated from the University of Michigan. This portfolio works to highlight some of my best projects over the past few years. I am proficient at coding in R, Python, SQL, and C++, with exposure to Java. I am looking for positions that can accentuate my strong communication skills, ability to present solutions in an easily digestable manner, and passion for finding real-world solutions behind the data provided to me. 

##### Contact Information:
Phone: (248) 231-6223  
Email: bbebb@umich.edu  
[LinkedIn](www.linkedin.com/in/brendanbebb)  
[LeetCode](https://leetcode.com/brendanbebb/)  

---------------

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

### Overview
This project was an independent research project completed and presented at the 2022 Michigan Sports Analytics Symposium. As a Baseball Analyst, I worked to propose and effectively answer several questions involving various trends across Major League Baseball, ranging from individual performance metrics to team-wide analyses.

### Individual Offensive Trends
Popularized by *Moneyball*, on-base percentage (OBP) became a more relevant metric for targeting players than slugging percentage (SLG) following the publication of the book. An alternative belief is that they should have direct correlation, and the more desired players have a high OBP and high SLG. As expected, there is a postivie correlation between OBP and SLG.  
  
Further analysis, however, is conducted on the everyday players from 2022. With popularity growing in 2022 for defensive shifting, run scoring came at an all-time premium. To combat this, players received better contracts if they hit for more power. Below, the graphs illustrate power hitters versus contact hitters and their respective relationships between OBP and SLG.

![Screen Shot 2023-07-25 at 12 53 34 PM](https://github.com/bbebb/bbebb.github.io/assets/73957927/4d1e3e3a-5b2d-42f8-a552-2f195582931f) ![Screen Shot 2023-07-25 at 12 54 40 PM](https://github.com/bbebb/bbebb.github.io/assets/73957927/e9969f60-7049-4871-95a6-d021676d21d1)

  
It is evident that both power hitters and contact hitters have similar correlations, but power hitters, as expected, have a higher slugging percentage, whereas contact hitters have a slightly higher on-base percentage.

### Team Defensive Trends
Following the same idea about the impact of defensive shifting, it is important to investigate the effects of shifting for a team's overall defensive performance. The notion behind the shift is that the more a team plays in a position that a player hits to most often, the more runs that will be saved defensively. The graph below illustrates the relationship amongst the 30 MLB teams in the 2022 season and the amount of times they shifted and the total number of defensive runs saved.

![Screen Shot 2023-07-25 at 1 18 25 PM](https://github.com/bbebb/bbebb.github.io/assets/73957927/f60ff179-7650-450f-b839-fd23214d3abe)


In order to save the most defensive runs possible, a team either shifted a minimal or maximal amount. Further trends and analyses, such as a breakdown of the best offensive team in the MLB and positional fielding evaluations, can be found in the accompanying repository for this project.  

## [Project 3: Identifying Optimal Regions for Economic Growth in the United States](https://github.com/bbebb/msa-research)

### Overview
Conducted in January of 2023, this academic research project cleans, manipulates, and evaluates a [dataset involving Metropolitan Statistical Areas](http://dept.stat.lsa.umich.edu/~bbh/s485/data/mobility1.csv) to determine the best region and nation to live in across the United States. One of the largest struggles individuals face in life is succeeding financially. In this project, I analyze the data of individuals from 40 different commuting zones across the nation to determine which region and [American nation](https://www.washingtonpost.com/blogs/govbeat/wp/2013/11/08/which-of-the-11-american-nations-do-you-live-in/) provides the best opportunity for one to move from the lowest economic quintile in their twenties to the highest economic quintile in their thirties.  

### Evaluating and Validating the Data
To ensure accurate results from the data, the 40 commuting zones are assigned their respective region and American naiton and grouped together. When grouped together by these criteria, one can see that the population sizes of the regions and nations are comparable, meaning that there is about an equal amount of individuals surveyed from each region, making these comparisons validated. 

### Utilizing the Jeffreys' Interval
After breaking up the data into the respective regions and nations, the Jeffreys' Interval (a variation of the common confidence interval) is calculated for each region/naiton to determine what proportion of the population moved from the lowest economic quintile to the highest economic quintile over the course of ten years, earning these individuals the title of "upmovers." The lower bound for the Jeffreys' Interval was calculated with the following formula, and the upper boundary was calculated in a similar manner.  

```{r}
JeffreysInterval_lower = function(n, k, phat) {
  x = phat * n
  alpha = (1 - k)/ 2
  kappa = qnorm(1 - alpha)
  w_t1 = ((kappa * sqrt(4 *  phat * (1 - phat)) / n) + ((kappa^2 - 3) / (6 * n^2))) / (4 * phat * (1 - phat))
  w_t2 = ((0.5 - phat) * (phat * (1-phat) * (kappa^2 + 2) - (1/n))) / (6 * n * (phat * (1-phat))^2)
  w = w_t1 + w_t2
  if (phat == 0) {
    lowerbound = 0
  }
  else if (phat == 1) {
    lowerbound = (x + 0.5) / (n + 1)
  }
  else {
    lowerbound = (x + 0.5) / (n + 1 +(n - x + 0.5) * (exp(2*w) - 1))
  }
  return(lowerbound)
}
```

### Results  
The proportion of upmovers obtained with the Jeffreys' Interval for the four major regions of the United States were as follows:  
  
<img width="371" alt="Screen Shot 2023-07-26 at 7 49 28 PM" src="https://github.com/bbebb/bbebb.github.io/assets/73957927/67be893d-2748-49d2-a85e-478eaf4f0ba0">  
  
The proportion of upmovers for the American nations were as follows:  

<img width="423" alt="Screen Shot 2023-07-26 at 7 49 37 PM" src="https://github.com/bbebb/bbebb.github.io/assets/73957927/f6d06a2d-46e1-4f17-9805-9fec8616b478">
  
As deduced from the tables, **the optimal region to live in for economic growth is the west region**, and **the optimal American nation to live in for economic growth is the El Norte Region**. However, the only issue with these results is that there is not a commuting zone that fits both of these criteria. The other bit of analysis worth mentioning is that it appears that grouping the United States by region is the most beneficial way to estimate the population proportion of upmover opportunities. 


## [Project 4: The Ultimate Piazza-Lecture Mashup: Your One-Stop Study Shop](https://github.com/JustinLocke/eecs486-finalProject)

### Overview
As a college student, the amount of material presented to review come exam time can be strenuous and require an ample amount of time to cover every possible source: lecture slides, discussion board threads, supplementary slides, lecture recording transcripts, and much more. During my Information Retrieval and Web Search course, a few of my classmates and I worked to implement a python program that scrapes the course website of all relevant course materials, tokenizes the text, and through both a custom Vector Space Model and generic Word2Vec VSM, evaluate the texts. Once the tokenization and evaluation is completed, the program returns the most relevant lecture slides, discussion board threads, and supplementary materials files that most closely match a user input query. Below is a map outlining the implementation route of this program. 
  
![Screen Shot 2023-07-26 at 8 30 06 PM](https://github.com/bbebb/bbebb.github.io/assets/73957927/3e87f387-208f-411e-aae8-eb638c5f5b1d)


### Methodology
1. Gather all course content with custom web scraper. *Note: in order to have this program run correctly, the user must have a valid login for the University of Michigan Canvas page.*
2. Create a Vector Space Model to weight and tokenize words from each dataset.
3. Weight the vectors using the tf-idf and word2vec algorithms.
4. Input a query of varying styles: administrative, conceptual, informative, etc.
5. Use cosine similarity scores to find the most relevant documents for the given query.
6. Evaluate the precision and recall scores for both weighting schemes used in the Vector Space Models.


### Model Analysis
The purpose of creating two Vector Space Models for this project was to see how beneficial the weighting scheme provided in the word2vec package in python is. In addition, the tf-idf weighting scheme specifically utilizes the ratio of thefrequency of a term in a document to the overall document length.  

![Screen Shot 2023-07-26 at 8 33 22 PM](https://github.com/bbebb/bbebb.github.io/assets/73957927/0a74b52f-5976-4b4b-967e-ce42f4292644)  

Above is a graphical representation of the cosine similarity scores obtained from the input query "calculate tf-idf." **Across all queries, the tf-idf model produced better precision and recall scores.** The conclusion reached about this is that the tf-idf model focuses more on the number of times a term appears in a document, whereas the word2vec model focuses on the distance between words in a sentence. In addition, queries that involve more conceptual wording seemed to produce better results for relevant documents. 


    


