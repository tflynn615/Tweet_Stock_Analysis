## Del 2 

### ML 
- Description of preliminary data preprocessing
  - the data pre-processing was done by first summing up the # of tweets for the day as `tweet_activity`and keeping the `date`, `volume` and `price-anction` for each ticker. Then seperating each ticker into their own csv file and exporting it to feed into the ML model.

- Description of preliminary feature engineering and preliminary feature selection, including their decision-making process
  - `tweet_activity` : was the tweet dataset summed up to it's most important factor because of it relation to the stock's price. selected as a feature.
  - `date`: trading date for each stock, was dropped when feeding it into the model because of it lack of importance to the model.
  - `volume`: a given tickers daily trading volume, used in the model as a feature.
  - `price-action`: very important features tells the price movement of the ticker in a given date. used in the model as a feature.
  - `liquid_lvl`: was the target of the dataset as the model was trying to predict how liquid the stock is given its `tweet_count`. 

- scription of how data was split into training and testing sets
  - the data for our model was split to the `train-test-split`'s default value, which allocates 75% of the data for trainig and 25% of testing.

- planation of model choice, including limitations and benefits
  - first `LinearRegression` was used to find a correlation in the dataset if any. `LinearRegression` although benifitial in looking at how one feature of the dataset influnces another, it's limited due to its simplicity and is unable to do a trainig and testing of the dataset. After finding a correlation between `volume` and `tweet-activity` `LogisticRegression` model was used to see how well the model could predict stock liquidity. `LogisticRegression` was successful in predicting a binary outcome, for our dataset it's limited by low accuracy score and ability to tweek the model.   
