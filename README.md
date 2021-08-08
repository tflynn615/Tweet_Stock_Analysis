# Twitter & Stock Price Analysis  

## Purpose 

The purpose of this project is to analyze the correlation, if any, that engagement/activity of a stock's ticker on Twitter has on it's selling activity on the NASDAQ. The question that we'd like to answer is: can we predict how much a stock will sell based on how it's trending on social media? 

## Technology 

  ### Data Cleaning and Analysis
  Excel csvs will be used to import the data and Pandas will be used to clean the data and perform an exploratory analysis. Further analysis and manipulation will be completed using Python before the data is imported to our PostgresSQL database. 


  Additionally VADER Sentiment Analysis will be used to get the overall sentiment of the tweet to turn string data into int data for a ML model & analysis.
  
  Sentiment includes Positive, Neutral, and Negative comments and will be derived to formulate impact onto stock market activity.


  ### Database Storage
  PostgreSQL is the database we intend to use, since we are working with ‘.csv’ data files. and we will integrate Tableau to display the data.


  ### Machine Learning
  SciKitLearn and Tensorflow will be the ML library we'll be using. Depending on what the data looks like after cleaning we will decide between a classification or a regression model. Machine Learning model diagram will be updated upon further discovery throughout the process.


  ### Dashboard
  Our final Dashboard will be presented on Tableau with all the findings and ML predictions.

## The Data 

The data that will be used in this analysis include a csv with opening/closing information for all NASDAQ, S&P500, and NYSE listed companies which is updated weekly. There are also csv's for tweets about the stock tickers of each of the top five technology companies (Amazon, Tesla, Google, Apple, Microsoft) from years 2015 to 2020. The planned ERD for the database that will connect each of these data sources looks like: 

![rough_stock_erd.png](Deliverable_1/ERD_v.1/rough_stock_erd.PNG)

## Machine Learning Model 

This analysis will use a neural network with Relu activation to model the correlation between volume of tweets and perception of tweets against the change in daily price. 

The current plan for the model is: 

Description of preliminary data preprocessing
 - the data pre-processing was done by first summing up the # of tweets for the day as `tweet_activity`and keeping the `date`, `volume` and `price-anction` for each ticker. Then seperating each ticker into their own csv file and exporting it into the ML model.

- Description of preliminary feature engineering and preliminary feature selection, including their decision-making process
  - `tweet_activity` : was the tweet dataset summed up to it's most important factor because of it relation to the stock's price. selected as a feature.
  - `date`: trading date for each stock, was dropped when feeding it into the model because of it lack of importance to the model.
  - `volume`: a given tickers daily trading volume, used in the model as a feature.
  - `price-action`: very important features tells the price movement of the ticker in a given date. used in the model as a feature.
  - `liquid_lvl`: was the target of the dataset as the model was trying to predict how liquid the stock is given its `tweet_count`. 

- Description of how data was split into training and testing sets
  - the data for our model was split to the `train-test-split`'s default value, which allocates 75% of the data for trainig and 25% of testing.

- Explanation of model choice, including limitations and benefits
  - first `LinearRegression` was used to find a correlation in the dataset if any. `LinearRegression` although benifitial in looking at how one feature of the dataset influnces another, it's limited due to its simplicity and is unable to do a trainig and testing of the dataset. After finding a correlation between `volume` and `tweet-activity` `LogisticRegression` model was used to see how well the model could predict stock liquidity. `LogisticRegression` was successful in predicting a binary outcome, for our dataset but it's limited by low accuracy score and inability to fine tune the model.  

- Explanation of changes in model choice (if changes occurred between the Segment 2 and Segment 3 deliverables)
  - for segment 3 a neural network model was added to improve accuracy score since `LogisticRegression` was only 57% accurate. The neural network uses one hidden layer and six neurons because of three input features for this model. This new model after 100 iterations gives us an accuracy socre of 97%.  

- Description of how they have trained the model thus far, and any additional training that will take place
  - the model was trained using `relu` in the hidden layer and `sigmoid` in the output layer as we need the model to tell us if the stock is either liquid or not. `StandardScaler` was used to scale training and testing the features. The model was ran for 100 epochs resulting in an accuracy score of 97%  

- Description of current accuracy score
  - As mentioned above the current model yeilds an accuracy score of 97%. Meaning the model can predict if a given stock is liquid (above avg daily volume ) feeding the dataset with extreme accuracy. 

## Presentation Slides

The presentation can also be accessed to its direct google slides link through the link below.
URL: https://docs.google.com/presentation/d/1eiDhg26rj6FX_s-b5r3N7FIJo1qq6LhwhcxKrEpWc80/edit#slide=id.g7ce6850189_0_111
