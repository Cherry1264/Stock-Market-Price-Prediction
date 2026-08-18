# Stock Market Price Prediction (Britannia — Linear Regression)

This repository contains a simple, notebook-first exploration that trains and evaluates a linear regression model to predict the closing price of Britannia stock from historical observations. It includes a Jupyter notebook with the analysis and a standalone Python script that reproduces the core workflow, together with a small example CSV dataset.

This project is educational: it's intended to show a minimal, end-to-end pipeline (EDA → modeling → evaluation → visualization) for stock-price forecasting using classical ML. It is not financial advice.

Contents
- Stock-Prices-Prediction-Using-Linear-Regression-main/
  - Britannia_Stock_Price_Prediction.ipynb — primary Jupyter notebook with step-by-step EDA, plots, and model training
  - Britannia Stock Market Prediction.py — standalone Python script that runs a linear regression experiment and produces plots/metrics
  - stock_val_march.csv — example data used by the notebook/script (OHLC/DATE/CLOSE etc.)
- README.md — this file

What this repo does (high level)
- Loads historical Britannia stock data (DATE, OPEN, HIGH, LOW, CLOSE, …)
- Runs exploratory data analysis and plots price series and distributions
- Trains a linear regression model (index → CLOSE) as a baseline
- Evaluates model performance using mean squared error (reported for train and test)
- Produces interactive/inline visualizations (plotly / matplotlib)

Quickstart (run the notebook — recommended)
1. Clone the repo
   git clone https://github.com/Cherry1264/Stock-Market-Price-Prediction.git
2. Create and activate a Python environment
   python -m venv .venv
   source .venv/bin/activate   # macOS / Linux
   .venv\Scripts\activate      # Windows
3. Install likely dependencies
   pip install pandas numpy matplotlib plotly scikit-learn jupyterlab
4. Start Jupyter and open the notebook
   jupyter lab
   Open: Stock-Prices-Prediction-Using-Linear-Regression-main/Britannia_Stock_Price_Prediction.ipynb
   Run cells in order.

Run the Python script (non-notebook)
- The script at Stock-Prices-Prediction-Using-Linear-Regression-main/Britannia Stock Market Prediction.py runs the same linear-regression experiment and prints MSE train/test. By default it attempts to read a CSV named `STOCK_VAL.csv`.
- The repository includes `stock_val_march.csv`. If you want to run the script directly, either:
  - Rename `stock_val_march.csv` to `STOCK_VAL.csv`, or
  - Edit the script to read `stock_val_march.csv` (change the filename on the pandas.read_csv line).

Notes about the implementation (observations from the code)
- Input target: the script uses the DataFrame index as the feature X and CLOSE as the target y, so the model is a simple index→price regression (a baseline).
- Scaling: StandardScaler is created but not applied to the regression input in the current script; you may want to scale features if you extend the experiment.
- Evaluation: mean squared error is printed for train and test; a "presicion_Score" is computed as test_score / train_score (ratio), which helps compare relative error but is not a standard classification metric.
- Visualization: uses plotly for interactive plots and matplotlib boxplots for price distributions.

Recommended improvements (if you want to extend)
- Use time-based features (lags, rolling means, returns) rather than index as the sole feature.
- Add a reproducible data-loading helper that accepts a path or ticker to avoid filename mismatches.
- Persist results (plots, model artifacts) into a results/ directory.
- Add a requirements.txt or environment.yml listing exact package versions.
- Add a short notebook cell that documents the dataset schema and required columns.

Data
- Example CSV included: Stock-Prices-Prediction-Using-Linear-Regression-main/stock_val_march.csv
- Not all datasets are provided; you can replace with historical OHLCV CSVs (yfinance, Alpha Vantage, etc.) as long as the notebook/script columns match.

License & contribution
- If you'd like this repo to be open-source, add a LICENSE (e.g., MIT).
- Contributions welcome: open issues or PRs for fixes, new model experiments (ARIMA, LSTM), or CI for reproducibility.

Contact
- Open an issue in this repository or reach out to the repo owner for questions.
