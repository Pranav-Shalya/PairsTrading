**📈 Pairs Trading Strategy using Cointegration (Python)**

**📌 Project Overview**

This project implements a Pairs Trading (Statistical Arbitrage) strategy using Python.
The objective is to identify cointegrated stock pairs from the Indian equity market and exploit mean-reversion in their price spread through a market-neutral long–short trading strategy.

Pairs trading is widely used by hedge funds and quantitative trading desks as it minimizes exposure to overall market movements and focuses on relative mispricing between assets.

**🎯 Problem Statement**

Financial markets often exhibit short-term inefficiencies where the relative prices of economically related stocks diverge temporarily.

The challenge is to:

Identify stock pairs that share a stable long-term relationship

Detect deviations from this equilibrium

Design a systematic strategy to profit when prices revert to their mean

**🧠 Key Concepts Used**

Correlation Analysis

Cointegration (Engle–Granger Test)

Stationarity & Mean Reversion

Hedge Ratio Estimation

Z-score based Trading Signals

Statistical Arbitrage

**📊 Dataset**

Universe: Selected stocks from the NIFTY 50 index

Source: Yahoo Finance (yfinance) and niftystocks

Frequency: Daily closing prices

Time Horizon: Multiple years of historical data

**🛠️ Tools & Technologies**

Python

Pandas & NumPy – Data manipulation and numerical computations

Statsmodels – Cointegration tests and regression

Matplotlib & Seaborn – Data visualization

YFinance / Niftystocks – Market data retrieval

**🔁 Project Workflow**

1️⃣ Data Collection & Preprocessing

Retrieved historical stock prices for all selected NIFTY stocks

Cleaned data by handling missing values and aligning time indices

Constructed a unified price DataFrame for analysis

2️⃣ Correlation Filtering

Computed pairwise Pearson correlations

Filtered pairs with high correlation to reduce computational complexity

Used this step as a pre-filter before cointegration testing

3️⃣ Cointegration Testing

Applied Engle–Granger cointegration test on correlated pairs

Selected pairs with statistically significant p-values (p < 0.05)

Ensured that selected pairs exhibit long-term equilibrium

4️⃣ Hedge Ratio Calculation

Estimated hedge ratio using:

𝛽
=
Cov
(
𝑌
,
𝑋
)
Var
(
𝑋
)

β=
Var(X)
Cov(Y,X)
	​


Hedge ratio determines the relative position sizing between two stocks

Used to construct a stationary spread

5️⃣ Spread Construction
Spread
=
𝑃
𝑟
𝑖
𝑐
𝑒
𝐴
−
𝛽
×
𝑃
𝑟
𝑖
𝑐
𝑒
𝐵
Spread=Price
A
	​

−β×Price
B
	​


The spread represents relative mispricing

Stationarity of the spread confirms mean reversion

6️⃣ Trading Strategy (Signal Generation)

Calculated Z-score of the spread:

𝑍
=
𝑆
𝑝
𝑟
𝑒
𝑎
𝑑
−
𝜇
𝜎

Z=
σ
Spread−μ
	​


Trading Rules:

Z-score > +1 → Short spread (Sell A, Buy B)

Z-score < –1 → Long spread (Buy A, Sell B)

Z-score ≈ 0 → Exit position

**7️⃣ Backtesting & Visualization**

Simulated trades using historical data

Visualized:

Price series of pairs

Spread and Z-score

Entry and exit points

Evaluated performance qualitatively and quantitatively

**📈 Key Insights**

High correlation does not guarantee cointegration

Cointegrated pairs are often from the same sector

Strategy performs best in sideways or range-bound markets

Mean reversion is the core profit driver

**⚠️ Challenges Faced**

Dependency conflicts (statsmodels, scipy)

Deprecated pandas functions (DataFrame.append)

Handling missing and misaligned time-series data

Preventing false positives in cointegration tests

**📚 Learnings**

Practical application of time-series econometrics

Importance of statistical validation before trading

Difference between correlation and cointegration

Real-world challenges of implementing quant strategies

🚀 Future Enhancements

Rolling-window cointegration testing

Dynamic hedge ratios using Kalman Filters

Incorporation of transaction costs and slippage

Sharpe ratio and drawdown analysis

Deployment via Streamlit dashboard

Extension to crypto and forex markets

**▶️ How to Run**

pip install -r requirements.txt
jupyter notebook

**📄 Requirements**
pandas
numpy
yfinance
statsmodels
matplotlib
seaborn

**👤 Author**

Pranav Shalya
Machine Learning & Quantitative Finance Enthusiast
