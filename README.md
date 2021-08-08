# Twitter & Stock Price Analysis  

## Purpose 

The purpose of this project is to analyze the correlation, if any, that engagement/activity of a stock's ticker on Twitter has on it's selling activity on the NASDAQ. The question that we'd like to answer are the follwowing: 

 - Can we predict how much a stock will sell based on how it's trending on social media?
 - Does tweets impact price action?

## Presentation Slides

The presentation can also be accessed to its direct google slides link through the link below.
URL: https://docs.google.com/presentation/d/1eiDhg26rj6FX_s-b5r3N7FIJo1qq6LhwhcxKrEpWc80/edit#slide=id.g7ce6850189_0_111

## Technology 

  ### Data Cleaning and Analysis
  Excel csvs from Kaggle were used to import the data for tweet data, and Yahoo Finance for stock data. `Pandas` was to clean the data and perform an exploratory analysis. Further analysis and manipulation was completed using Python before the data was imported to our PostgresSQL database and connected to our machine learning model. 

  ### Database Storage
  The database utilized was PostgresSQL with pgadmin 4. Data collected from Kaggle and Yahoo Finance were cleaned during the pre-processing stages with `pandas` and brought into our environment. 5 Ticker tables were brought into our database, 1 for each ticker, and further consolidated to form our master table data. Postgres database was then connected our our machine learning ipynb file for further analysis for prediction and accuracy.

  ### Machine Learning
  SciKitLearn and Tensorflow is the ML library utilized. Machine Learning models utilized were `Linear Regression`, `Logistic Regression`, and `Artifical Neural Network`.


  ### Dashboard
  Our final Dashboard is LIVE and available on Tableau public with our findings and ML predictions. Analysis includes dynamic integrations between tweet, date, and stock ticker to provide visual grasp to our end users on how tweets and the stock exchange share a relationship in stock liquidity. Analysis of our findings include Tweet Impacts on Stock Prices and Examining Tweet Engagement. Our visualizations can be found by clicking the link below.
  **URL**: https://public.tableau.com/app/profile/tara.flynn/viz/Bootcamp_Roughdraft/Dashboard1
  
## The Data 

The data that will be used in this analysis include a csv with opening/closing information for all NASDAQ, S&P500, and NYSE listed companies which is updated weekly. There are also csv's for tweets about the stock tickers of each of the top five technology companies (Amazon, Tesla, Google, Apple, Microsoft) from years 2015 to 2020. The planned ERD for the database that will connect each of these data sources looks like: 

![rough_stock_erd.png](Deliverable_1/ERD_v.1/rough_stock_erd.PNG)

## Machine Learning Model 

This analysis will use a neural network with Relu activation to model the correlation between volume of tweets and perception of tweets against the change in daily price. 

**Description of preliminary data preprocessing:**
 - the data pre-processing was done by first summing up the # of tweets for the day as `tweet_activity`and keeping the `date`, `volume` and `price-anction` for each ticker. Then seperating each ticker into their own csv file and exporting it into the ML model.

**Description of preliminary feature engineering and preliminary feature selection, including their decision-making process**
 - `tweet_activity` : was the tweet dataset summed up to it's most important factor because of it relation to the stock's price. selected as a feature.
 - `date`: trading date for each stock, was dropped when feeding it into the model because of it lack of importance to the model.
 - `volume`: a given tickers daily trading volume, used in the model as a feature.
 - `price-action`: very important features tells the price movement of the ticker in a given date. used in the model as a feature.
 - `liquid_lvl`: was the target of the dataset as the model was trying to predict how liquid the stock is given its `tweet_count`. 

**Description of how data was split into training and testing sets:**
 - the data for our model was split to the `train-test-split`'s default value, which allocates 75% of the data for trainig and 25% of testing.

**Explanation of model choice, including limitations and benefits:**
 - first `LinearRegression` was used to find a correlation in the dataset if any. `LinearRegression` although benifitial in looking at how one feature of the dataset influnces another, it's limited due to its simplicity and is unable to do a trainig and testing of the dataset. After finding a correlation between `volume` and `tweet-activity` `LogisticRegression` model was used to see how well the model could predict stock liquidity. `LogisticRegression` was successful in predicting a binary outcome, for our dataset but it's limited by low accuracy score and inability to fine tune the model.  

**Explanation of changes in model choice (if changes occurred between the Segment 2 and Segment 3 deliverables):**
 - for segment 3 a neural network model was added to improve accuracy score since `LogisticRegression` was only 57% accurate. The neural network uses one hidden layer and six neurons because of three input features for this model. This new model after 100 iterations gives us an accuracy socre of 97%.  

**Description of how they have trained the model thus far, and any additional training that will take place:**
 - the model was trained using `relu` in the hidden layer and `sigmoid` in the output layer as we need the model to tell us if the stock is either liquid or not. `StandardScaler` was used to scale training and testing the features. The model was ran for 100 epochs resulting in an accuracy score of 97%  

**Description of current accuracy score:**
 - As mentioned above the current model yields an accuracy score of 97%. Meaning the model can predict if a given stock is liquid (above avg daily volume ) feeding the dataset with extreme accuracy. 
