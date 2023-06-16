### Group_5_Project_2
# Algorithmic Trading Strategy Optimization for FAANG Stocks
![FAANG-stocks](https://github.com/AthuraThava/Group_5_Project_2/assets/125109159/11ac0756-0815-4d7f-8565-cc884b0ea0f0)

**Team Members:** <br>
Athura Thavathasan <br>
Brandon Petrie <br>
Harshitha Katta <br>
Nicholas Gracan <br>
Pablo Acevedo <br>
*Presentation June 15th, 2023*

### To access the presentation use the following link: 
[import link/file](https://docs.google.com/presentation/d/1PmvzF5GRk6fXmAmKf6NDKacA07nCLFucnHAD2ST3_Yg/edit?usp=sharing)

## Hypothesis
The project focuses on creating an algorithmic trading system with a specific emphasis on FAANG stocks (Facebook, Apple, Amazon, Netflix, and Google). The primary objective is to conduct thorough backtesting and market analysis using historical data of these stocks. By employing various trading models, the project aims to develop accurate predictions and optimize trading strategies. Technical indicators such as Simple Moving Average (SMA) and logistic regression are utilized to enhance the models' predictive capabilities. Through extensive backtesting and model development, the project seeks to identify buy or sell signals for each FAANG stock, enabling informed trading decisions. The ultimate goal is to create a robust and effective algorithmic trading system that can generate profitable results based on market analysis and strategy optimization.  <br>

## Datasets
To retrieve historical stock data, we utilize the yfinance library. By importing `import yfinace as yf` library and providing the needed ticker symbols `META``AAPL``AMZN``NFLX``GOOGL` it allowed us to fetch data directly from Yahoo Finance, providing us with a convenient and reliable source of historical stock prices for analysis and modeling. 

# Libraries 
## Import Libraries
* import `pandas` as `pd` (Used for data manipulation and analysis)
* import `yfinance` as `yf` ( to fetch historical stock price data of FAANG stocks)
* import `finta` (Used for technical analysis for indicators such as SMA, EMA and Boolinger Bands)
* import `plotly.graph_objects` as `go`
* from `pandas.tseries.offsets` import `DateOffset`
* from `sklearn.preprocessing` import `StandardScaler`
* from `sklearn.metrics` import `classification_report`
* from `sklearn` import `svm`
* from `sklearn.svm` import `SVC`

## Models
Support Vector Machine (SVM):  It is a robust model that is used to predict whether the share’s close price will be higher or lower than the day before. We used SVM because it allows us to compare with multiple indicators because it can handle more complex data.

Logistic Regression:  Logistic regression will allow us to hone in specifically on the direction of share price and by leaving other factors like momentum or strength of movement out, therefore the accuracy of direction will increase.

## Data Analysis
Retrieved historical data for FAANG stocks using the `yf.download` function from the `yfinance` library. The data is retrieved for the time period from `start_date` July 1, 2021, to `end_date` June 1, 2023, at an hourly interval.

Computed various technical analysis indicators such as Simple Moving Averages (SMA) and Exponential Moving Average (EMA) for each stock. 

Using the `go.Candlestick` class from the `plotly.graph_objects` library visualized the stock price and creates a candlestick chart. The chart helps visualize the stock's price movements and the trend indicated by the moving averages.

Dropping unnecessary columns from the DataFrame and preparing the data for training and testing the machine learning model.

Initializes a new column called 'signal' in the DataFrame and assigns signals (-1 for sell and 1 for buy) based on the comparison between SMA, EMA, and the stock price. The code generates trading signals based on the relationship between the SMAs and EMA. If both the SMA_9 and SMA_21 are below the EMA_200, a sell signal (-1) is assigned. If both SMAs are above the EMA_200, a buy signal (1) is assigned. The generated signals are stored in the `signal` column of the DataFrame

# Model Training
Splitting the data into training and testing sets, with the training set covering a 3-month period from the start of the data. The code prepares the data for model training and testing. The signal column is copied to a new Series called 'y', and the SMA_9, SMA_21, and EMA_200 columns are selected and copied to a new DataFrame called 'X'. The data is split into training and testing sets based on the specified time periods.

Applied feature scaling to the training and testing data using the `StandardScaler` from `sklearn.preprocessing` to normalize the input features. The code applies the StandardScaler to scale the features (SMA_9, SMA_21, EMA_200) in the training and testing data. The code creates an SVM model (SVC()) and fits it to the scaled training data. 

Created an SVM classifier (`SVC` class from `sklearn.svm`) and fit it to the training data.

The trained SVM model will predict the trading signals for both the training and testing data. The predictions are stored in `training_signal_predictions` and `testing_signal_predictions`

# Evaluation

Evaluated the model's performance by generating a classification report for both the training and testing data, which provides metrics such as precision, recall, F1-score, and accuracy. The classification report evaluates the model's performance in predicting the trading signals.

Created a new DataFrame `predictions_df` for predictions, which includes the predicted signals, actual returns, and algorithmic trading returns.

Plotted the cumulative returns for the actual returns and the trading algorithm returns.
=======
### 1 Hour
![AAPL Classification Report](Images/1h/AAPL_Classification%20Report_1h.png)

![AAPL Cumulative Returns Plot](Images/1h/AAPL_cumulative_returns_plot_1h.png)

![AAPL Cumulative Returns Plot LR1h](Images/1h/AAPL_cumulative_returns_plot__LR1h.png)

![AAPL with SMAs EMA200](Images/1h/AAPL_with_SMAs_EMA200_1h.png)

![AMZN Classification Report](Images/1h/AMZN_Classification%20Report_1h.png)

![AMZN Cumulative Returns Plot](Images/1h/AMZN_cumulative_returns_plot_1h.png)

![AMZN Cumulative Returns Plot LR1h](Images/1h/AMZN_cumulative_returns_plot__LR1h.png)

![AMZN with SMAs EMA200](Images/1h/AMZN_with_SMAs_EMA200_1h.png)

![GOOG Classification Report](Images/1h/GOOG_Classification%20Report_1h.png)

![GOOG Cumulative Returns Plot](Images/1h/GOOG_cumulative_returns_plot_1h.png)

![GOOG Cumulative Returns Plot LR1h](Images/1h/GOOG_cumulative_returns_plot__LR1h.png)

![GOOG with SMAs EMA200](Images/1h/GOOG_with_SMAs_EMA200_1h.png)

![META Classification Report](Images/1h/META_Classification%20Report_1h.png)

![META Cumulative Returns Plot](Images/1h/META_cumulative_returns_plot_1h.png)

![META Cumulative Returns Plot LR1h](Images/1h/META_cumulative_returns_plot__LR1h.png)

![META with SMAs EMA200](Images/1h/META_with_SMAs_EMA200_1h.png)

![NFLX Classification Report](Images/1h/NFLX_Classification%20Report_1h.png)

![NFLX Cumulative Returns Plot](Images/1h/NFLX_cumulative_returns_plot_1h.png)

![NFLX Cumulative Returns Plot LR1h](Images/1h/NFLX_cumulative_returns_plot__LR1h.png)

![NFLX with SMAs EMA200](Images/1h/NFLX_with_SMAs_EMA200_1h.png)

### 5 Minutes
![AAPL Classification Report](Images/5m/AAPL_Classification%20Report_5m.png)

![AAPL Cumulative Returns Plot](Images/5m/AAPL_cumulative_returns_plot_5m.png)

![AAPL Cumulative Returns Plot LR5m](Images/5m/AAPL_cumulative_returns_plot__LR5m.png)

![AAPL with SMAs EMA200](Images/5m/AAPL_with_SMAs_EMA200_5m.png)

![AMZN Classification Report](Images/5m/AMZN_Classification%20Report_5m.png)

![AMZN Cumulative Returns Plot](Images/5m/AMZN_cumulative_returns_plot_5m.png)

![AMZN Cumulative Returns Plot LR5m](Images/5m/AMZN_cumulative_returns_plot__LR5m.png)

![AMZN with SMAs EMA200](Images/5m/AMZN_with_SMAs_EMA200_5m.png)

![GOOG Classification Report](Images/5m/GOOG_Classification%20Report_5m.png)

![GOOG Cumulative Returns Plot](Images/5m/GOOG_cumulative_returns_plot_5m.png)

![GOOG Cumulative Returns Plot LR5m](Images/5m/GOOG_cumulative_returns_plot__LR5m.png)

![GOOG with SMAs EMA200](Images/5m/GOOG_with_SMAs_EMA200_5m.png)

![META Classification Report](Images/5m/META_Classification%20Report_5m.png)

![META Cumulative Returns Plot](Images/5m/META_cumulative_returns_plot_5m.png)

![META Cumulative Returns Plot LR5m](Images/5m/META_cumulative_returns_plot__LR5m.png)

![META with SMAs EMA200](Images/5m/META_with_SMAs_EMA200_5m.png)

![NFLX Classification Report](Images/5m/NFLX_Classification%20Report_5m.png)

![NFLX Cumulative Returns Plot](Images/5m/NFLX_cumulative_returns_plot_5m.png)

![NFLX Cumulative Returns Plot LR5m](Images/5m/NFLX_cumulative_returns_plot__LR5m.png)

![NFLX with SMAs EMA200](Images/5m/NFLX_with_SMAs_EMA200_5m.png)


## Discussion/ Conclusion
From the SVM model we used two sets of controlled variables with the time frame intervals: 1H and 5m.  As we can see from the chart above, the 1H model produced sub par results at about 50% accuracy.  It should be noted that for all 5 stocks the model came back with similar results.

Initially the points where SMA 9 and SMA 21 intersected was going to be used to determine the entry and exit points using EMA 200 as a base line.

However there wasn’t enough points of references to output this data since the interval was broader and focused at 1 day intervals.
The constraints to determine the entry and exit points were altered in order to run backtesting and assign signal values of -1, and 1.
The new points didn’t require SMA 9 and SMA 21 to crossover. It was only required that both SMAs were above or below the EMA200 at the same time.

Hence we ran 2 codes where the intervals were 1 hour and 5 mins apart with the data windows previously explained. The 5min interval plot didn’t correlate with the classification reports for Amazon and Google Stocks. 
Taking these factors into consideration we determined that the 1 hour interval contained more historical data and that a correlation between the classification report accuracy and the plot was present. 
Even though the accuracy was lower, this may be attributed to the fact that we changed the entry and exit constraints to a broader one.

The SVM returns similar results amongst the different companies, even though the results aren't reliable.  The results from the ogistic regression were random amongst the 5 different companies. Ranging from poor to good with 4⁄5 companies returning insufficient results.  In other words the logistic regression results were neither precise nor accurate.

## PostMortem

### Difficulties/ Limitations
* Importing data on a larger scale, more historically data with small intervals
* Implement the initial constraints on strategies 
* Backtest the other indicators (MACD, Bollinger Bands, Williams Fractals)
* Combine strategies into one to establish more accuracy
* Feeding data and strategy into a trading bot, that will output exit and enter points for real-time data.

### Furthur Findings: What would you research next if you had two more weeks?:
* There is a lot more opportunity to build on. To implement additional technical indicators or develop custom features that might provide valuable insights for trading strategies. Consider indicators such as Relative Strength Index (RSI), by incorporating these features it could improve the accuracy of the models.
* Sentiment analysis techniques to incorporate real-time market data from news articles, social media, or financial reports. Determine whether sentiment analysis can enhance the prediction accuracy of the trading models and potentially provide early indications of market movements.
* Implement a trading bot in real-time scenarios, connecting it to live market data and executing trades automatically.

### Referneces 
* University of Toronto Bootcamp. (2023). FinTech. Retrieved from [https://bootcamp.utoronto.ca/data/](https://utoronto.bootcampcontent.com/utoronto-bootcamp/UTOR-VIRT-FIN-PT-02-2023-U-LOLC)https://utoronto.bootcampcontent.com/utoronto-bootcamp/UTOR-VIRT-FIN-PT-02-2023-U-LOLC
* Pandas:
  * Pandas. (n.d.). Retrieved from https://pandas.pydata.org/
* yfinance:
  * Ranaroussi, R. (n.d.). yfinance. Retrieved from https://github.com/ranaroussi/yfinance
* finta:
  * Peerchemist. (n.d.). finta. Retrieved from https://github.com/peerchemist/finta
* Plotly:
  * Plotly. (n.d.). Retrieved from https://plotly.com/python/
* scikit-learn (sklearn):
  * scikit-learn. (n.d.). Retrieved from https://scikit-learn.org/stable/

