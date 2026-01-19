# Arbitron Systems Quantitave Finance Pipeline

Hi everyone. This is the AS Q Pipeline repository, a quantitative trading system that is processing raw data furthermore signal generation and backtesting.

The project is built on the Qlib framework. The code is currently in the MVP stage and requires refactoring, but the architecture is fully functional and demonstrates stable alpha on historical data.

## Technical Stack and Implementation Details

#### Data and Feature Engineering: 
Uses the Alpha158 factor set (158 technical indicators, including Momentum, Volatility, and Volume patterns). Data consists of daily quotes from the CSI300 Public Dataset.

#### Preprocessing: 
RobustZScoreNorm for outlier removal and CSRankNorm for the target variable. The model learns to predict the relative rank of a stock within the cross-section, which maximizes the Rank IC.

#### Model: 
LightGBM. Chosen for its efficiency on noisy tabular data and performance.

#### Backtest Engine: 
TopkDropout strategy (holding the top-N stocks based on the predicted scores).

## Results (Backtest 2017–2020)
On the test set, the pipeline achieves the following metrics:

#### Information Coefficient (IC): ~0.047 (Strong Signal)
#### Excess Return (Alpha): ~175% (Strategy outperformed the benchmark by ~2.7x)

Screenshots of Cumulative Return and IC Analysis charts are provided below.

![IC Report](https://github.com/arbitrum1984/AS_quant_pipeline/blob/main/screenshots/ic_report.png)

![Strategy Performance](https://github.com/arbitrum1984/AS_quant_pipeline/blob/main/screenshots/strategy_performance.png)
##  How to Run

To run the pipeline, simply install the dependencies. Python 3.8+ is recommended.

```bash
# 1. Clone the repository
git clone https://github.com/arbitrum1984/AS_quant_pipeline/

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the pipeline (Train + Backtest)
python main.py
```
