# LSTM Neural Network for Predicting Stock Price Movements Using State

This trading strategy is designed for the [Quantiacs](https://quantiacs.com/contest) platform, which hosts competitions
for trading algorithms. Detailed information about the competitions is available on
the [official Quantiacs website](https://quantiacs.com/contest).

## How to Run the Strategy

### In an Online Environment

The strategy can be executed in an online environment using Jupiter or JupiterLab on
the [Quantiacs personal dashboard](https://quantiacs.com/personalpage/homepage). To do this, clone the template in your
personal account.

### In a Local Environment

To run the strategy locally, you need to install the [Quantiacs Toolbox](https://github.com/quantiacs/toolbox).

## Strategy Overview

This notebook demonstrates the use of a **Long Short Term Memory (LSTM) Neural Network** to predict stock price movements. It focuses on trading the top NASDAQ-100 stocks with the lowest volatility, leveraging previous weights to determine positions for the next day.

### Key Features:
- **Universe:** NASDAQ-100 stocks
- **Trading Logic:** Long positions based on the LSTM model’s prediction confidence level.
- **Feature for Learning:** Trend calculated using the rate of change (ROC) of the logarithm of the closing price with a linear weighted moving average (LWMA).

### Strategy Components:
1. **Data Loading and Preparation:** 
   - Load stock data using `qndata.stocks.load_ndx_data`.
   - Calculate features using `qnta.lwma` and `qnta.roc`.
   - Determine target classes for price movement prediction.

2. **LSTM Model Definition:** 
   - Define the LSTM architecture with input, hidden, and output layers.
   - Implement training using Mean Squared Error (MSE) loss and L-BFGS optimizer.

3. **Model Training:**
   - Filter data to focus on top assets with the lowest volatility.
   - Train models for each asset in the dataset.

4. **Prediction and State Management:**
   - Use trained models to predict future price movements.
   - Combine predictions with previous weights to determine final positions.
   - Save and load state.

5. **Backtesting:**
   - Multi-pass version for development and testing.
   - Single-pass version for competitive submissions to expedite processing.

### Recommendations for Competitive Submissions:
- Simplify models to reduce computational demand.
- Enhance local development with high-performance computing resources.
- Utilize pre-calculated indicators.

### Additional Resources:
- **Quantiacs Community Topics:**
  - [Backtest ML Runtime Optimization](https://quantiacs.com/community/topic/528/backtest_ml-has-too-long-a-run-time/3)
  - [Printing Training Performance](https://quantiacs.com/community/topic/537/printing-training-performance-of-neural-network-models)
  - [Accessing Previous Weights](https://quantiacs.com/community/topic/555/acess-previous-weights)
