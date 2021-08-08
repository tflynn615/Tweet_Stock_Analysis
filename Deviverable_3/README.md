## Deliverable 3

### Database Connection
Data collected from Kaggle and Yahoo Finance were cleaned using `pandas` and brought into our postgress sql database, `pgadmin 4`. Ticker tables (x5) were brought into our database and consolidated to form our master table data using postgres and connected to our ipynb file for machine learning.


### Machine Learning 
- Description of preliminary data preprocessing
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

### Dashboard and Analysis

#### Tweet Volume

![tweet_volume.png](../analysis_images/tweet_volume.png) 

_Purpose:_ Find which companies are receiving the most tweets and interactions. 

_Analysis:_ 
- Sum of all tweets 2015-2019 
- Color by sum of likes, comments, and retweets 
