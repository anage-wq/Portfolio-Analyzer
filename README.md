# Portfolio Analysis and XIRR Calculation Repo

This repository contains Python scripts and a Jupyter Notebook aimed at analyzing stock portfolios and index funds with a focus on volatility, maximum drawdown, and Extended Internal Rate of Return (XIRR). The tools use Yahoo Finance data and support detailed portfolio performance metrics specifically tailored for Indian stock symbols (with NSE/BSE exchange suffixes).

---

## Files Overview

### 1. `portfolio_volatility-drawdown_analysis.py`

- Implements functions to calculate portfolio volatility and maximum drawdown over customizable periods.
- Fetches historical stock data from Yahoo Finance (NSE symbols by default).
- Analyzes individual stocks as well as overall portfolio metrics by weighting stocks based on quantity and current prices.
- Supports multiple periods for analysis (e.g., 3 months, 6 months, 1 year).
- Outputs individual stock volatility, max drawdown, and aggregated portfolio risk metrics.
- Includes utility functions for data fetching, volatility calculation (annualized), max drawdown, and weighted portfolio analysis.

### 2. `index_funds_vol-dd.ipynb`

- Jupyter Notebook providing an interactive exploratory analysis of index funds like NIFTYBEES, BANKBEES, MID150BEES, and HDFCSML250.
- Calculates and displays volatility and max drawdown statistics for these ETF/index funds over different time periods.
- Structured with clear modular classes: `StockDataFetcher`, `VolatilityCalculator`, `DrawdownCalculator`, and `PortfolioAnalyzer`.
- Outputs period-wise volatility and max drawdown values along with weighted portfolio metrics for index funds.
- Suitable for quick visual turn-key analysis of portfolio risk metrics in an index fund context.

### 3. `portfolio_vol-dd_preprocessing.py`

- Contains data preprocessing pipeline components for portfolio trade data.
- Cleans and converts quantities and price columns to numeric types.
- Includes utility functions for JSON reading, adjusting quantities with external data, and fetching latest close prices from Yahoo Finance.
- Designed to prepare raw trade and holding data for subsequent detailed analysis.
- Integrates well with the volatility and drawdown scripts providing sanitized input data frames.

### 4. `portfolio_xirr.py`

- Contains a comprehensive implementation for calculating the XIRR of a portfolio.
- Uses classes with single responsibilities: data preprocessing, symbol resolution, stock split adjustment, cash flow calculation, and XIRR calculation.
- Resolves symbol ambiguities especially for Indian stock exchange suffixes NSE (.NS) and BSE (.BO).
- Adjusts trades for stock splits to ensure accurate cash flow representation.
- Fetches current prices from Yahoo Finance and combines with historical trades to calculate realistic XIRR including unrealized holdings.
- Includes error handling and fallback mechanisms for missing prices or delisted stocks.
- The main script uses a trade book CSV and external split JSON to calculate and print portfolio XIRR.

### 5. `xirr_for_indexes.py`

- Specialized script to compute XIRR for a set of index fund securities like NIFTYBEES, BANKBEES, MID150BEES, HDFCSML250.
- Calculates net cash flows from a tradebook and combines with current market prices fetched from Yahoo Finance.
- Uses numerical optimization (Newton's method) to find the internal rate of return.
- Handles timezone-aware datetimes and sorts cash flow events for accurate calculation.
- Provides convenience functions to fetch current prices and clean trade data inputs.
- Designed for index fund-focused investors to
