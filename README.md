<p align="center">
  <a href="https://www.kaggle.com/code/hassanjameelahmed/intel-stock-price-full-historical-market-2000-2026" target="_blank">
    <img src="2008.png" alt="PepsiCo" alt="PepsiCo" width="500">
  </a>
</p>
<br>

## INTC Historical Stock Prices: Intel Corporation (2000–2026)

### 1. Project Overview (PRD)

- **Project goal**: Build a clean, well-documented daily time-series dataset of Intel Corporation’s (`INTC`) historical stock prices and trading activity from 01/03/2000 to 01/30/2026, suitable for exploratory data analysis, forecasting models, financial research, and Kaggle competitions.
- **Primary use cases**:
  - **Price forecasting & time-series modeling**: ARIMA, Prophet, LSTM, Transformers, etc.
  - **Volatility and risk analysis**: rolling volatility, drawdowns, Value-at-Risk style studies.
  - **Event and regime analysis**: impact of macro events, earnings, and technology cycles on INTC.
  - **Educational use**: teaching financial data handling, feature engineering, and backtesting.
- **Target users**: Data scientists, quantitative researchers, students, ML practitioners, and Kaggle competitors interested in equity markets and large-cap technology stocks.

### 2. Dataset Summary

- **Entity**: Intel Corporation common stock (`INTC`).
- **Frequency**: Daily trading days (no weekends or market holidays).
- **Period covered**: From **01/03/2000** to **01/30/2026**.
- **Exchange**: U.S. stock market (NASDAQ/NYSE; U.S. equity market hours).
- **Geographical focus**: Intel as a global company listed in the **United States** (New York–based exchanges).
- **File format**: CSV (`INTC.csv`).

The dataset provides daily Open, High, Low, Close prices and traded Volume for Intel, enabling classical OHLCV-based analysis.

### 3. Column Definitions (Kaggle-Style Schema)

Source header:

```text
Date,Close,High,Low,Open,Volume
```

Detailed column documentation:

| Column | Type   | Format / Unit     | Example       | Description |
|--------|--------|-------------------|---------------|-------------|
| `Date` | string | `M/D/YYYY`        | `1/3/2000`    | Trading calendar date for each observation. Only business days on which the U.S. equity market is open are included. |
| `Close` | float | USD               | `24.71065521` | Closing price of INTC on that trading day, in U.S. dollars. Typically corresponds to the last traded price during regular market hours as provided by the data source. |
| `High` | float | USD               | `24.81716666` | Highest traded price during the trading session for that date. |
| `Low` | float | USD               | `23.64554076` | Lowest traded price during the trading session for that date. |
| `Open` | float | USD               | `23.64997874` | Opening price at the start of the regular trading session for that date. |
| `Volume` | integer | shares traded | `57710200`    | Total number of INTC shares traded during that trading day (raw volume count). |

Notes:

- **Data types**: `Date` can be parsed into a date or datetime type; price columns (`Open`, `High`, `Low`, `Close`) should be parsed as floating-point numbers; `Volume` as integer or 64-bit integer.
- **Sorting**: Rows are naturally sorted by `Date` in ascending order from 2000 to 2026.

### 4. Kaggle Dataset Metadata

#### 4.1 Suggested Kaggle Tags (Top 5)

- **Tag 1**: `stock-market-data`
- **Tag 2**: `time-series`
- **Tag 3**: `finance`
- **Tag 4**: `intel`
- **Tag 5**: `technology-sector`

These tags help Kaggle users quickly discover the dataset for financial, time-series, and technology-related projects.

#### 4.2 SEO-Optimized Project Name and Description

- **Project / Dataset name**:  
  **“INTC Stock Price History (2000–2026): Daily Intel Corporation OHLCV Dataset”**

- **Short, SEO-friendly description**:  
  **“Daily Intel Corporation (INTC) stock prices with Open, High, Low, Close, and Volume from 01/03/2000 to 01/30/2026, ideal for time-series forecasting, trading strategy backtesting, volatility analysis, and financial ML projects on Kaggle.”**

Keywords included: `Intel`, `INTC`, `stock price history`, `daily`, `OHLCV`, `time series`, `Kaggle`, `trading`, `backtesting`, `forecasting`.

### 5. Coverage

- **Asset coverage**: Single large-cap U.S. technology stock – Intel Corporation (`INTC`).
- **Temporal coverage**:  
  - Start date: **01/03/2000** (first row in `INTC.csv`).  
  - End date: **01/30/2026** (last complete row in `INTC.csv`).  
  - Approx. 26 years of daily trading history.
- **Feature coverage**:
  - **Prices**: Opening, highest, lowest, and closing price per day.
  - **Liquidity**: Daily trading volume.
- **Market coverage**: Only regular-session daily bars for the primary U.S. listing; no after-hours data.

### 6. Temporal and Geospatial Scope

- **Temporal scope**:
  - **Start date (MM/DD/YYYY)**: **01/03/2000**
  - **End date (MM/DD/YYYY)**: **01/30/2026**
  - **Granularity**: Daily (one record per trading day).

- **Geospatial scope**:
  - **Primary market location**: **New York, United States** (U.S. stock exchanges such as NASDAQ/NYSE, where INTC is listed and traded).
  - **Relevant country**: **United States**
  - While Intel is a global company, the dataset focuses specifically on the trading activity of its stock on U.S. exchanges.

### 7. Provenance and Source

- **Underlying data source (provenance)**:
  - The dataset is derived from publicly available **historical price data for Intel Corporation (ticker: INTC)** provided by **Yahoo Finance**.
  - Public historical data is typically accessed via the **“Historical Data”** section of the Intel ticker page.
- **Canonical source link**:
  - `https://finance.yahoo.com/quote/INTC/history`

- **Transformation steps** (from raw source to `INTC.csv`):
  1. Navigate to the Intel Corporation historical data page on Yahoo Finance (see link above).
  2. Select the desired **date range** (from 01/01/2000 to the most recent available date) and **daily frequency**.
  3. Export/download the data as CSV.
  4. Optionally reorder and select relevant columns to match the final schema: `Date, Close, High, Low, Open, Volume`.
  5. Save the cleaned file as `INTC.csv` without altering the numerical values of prices or volume.

This provenance description helps users understand that the dataset reflects official market data as aggregated and published by Yahoo Finance, which itself sources prices and volumes from major U.S. exchanges and market data providers.

### 8. Dataset Collection Methodology

- **Collection mode**:
  - Data is collected via **bulk CSV download** from Yahoo Finance’s historical data interface (manual) or via scripted HTTP requests to the same underlying endpoint (programmatic).
- **Sampling frequency**:
  - **Daily**: each row corresponds to one trading day; non-trading days are not included.
- **Data processing decisions**:
  - Only the following columns are retained: `Date`, `Close`, `High`, `Low`, `Open`, `Volume`.
  - No resampling, interpolation, or forward-filling of missing days is performed; missing days correspond to market holidays and weekends.
  - Prices remain in **USD** and volume in **number of shares**, consistent with the source.
- **Quality checks**:
  - Verifying that `Low <= Open, Close, High` and `High >= Open, Close, Low` for each row.
  - Ensuring chronological ordering from earliest to latest date.
  - Spot-checking a sample of days against the Yahoo Finance web interface for consistency.

Geographically, the data represent trades executed on U.S. exchanges for INTC; no other country’s exchanges are included.

### 9. Biggest Problems and Challenges

- **Non-stationary behavior and regime shifts**:
  - Over 26 years, INTC’s price dynamics are affected by multiple regimes: dot-com bubble, 2008 financial crisis, semiconductor cycles, COVID-19 volatility, and evolving competitive landscape. Models assuming stationarity will struggle.

- **Single-asset focus**:
  - The dataset only contains Intel; there is no market index (e.g., S&P 500, NASDAQ), peer stocks, or macroeconomic variables. This limits relative-performance analysis and may encourage overfitting to idiosyncratic noise.

- **Survivorship and selection bias**:
  - Focusing only on a successful, continuously listed large-cap stock introduces survivorship bias and may not represent the broader behavior of equities that delist or underperform.

- **Corporate actions and structural breaks**:
  - Stock splits, dividends, and other corporate actions can cause structural breaks in price levels and volatility. If users do not carefully handle these, models may misinterpret level shifts as genuine new regimes.

- **Predictability vs. market efficiency**:
  - Financial markets are competitive and noisy. Even with a long, rich dataset, building models that truly generalize and outperform simple baselines is challenging due to the efficient market hypothesis and transaction costs.

- **Data granularity limitations**:
  - Daily data may be too coarse for high-frequency strategies and too detailed for long-horizon asset allocation without additional aggregation or features.

### 10. How the Problem Developed (Step-by-Step)

This section explains how the **project problem** and dataset needs developed over time:

1. **Identifying the business and research question**  
   - Stakeholders are interested in **understanding and forecasting the behavior of Intel’s stock price** over multiple market cycles. They want a dataset that supports exploratory analysis, backtesting, and ML modeling.

2. **Recognizing the need for a clean, public time-series dataset**  
   - To answer these questions, we require **long-horizon, daily-level historical data** that is **public, reproducible, and easy to access** for anyone (e.g., Kaggle users, students, and researchers).

3. **Evaluating potential data sources**  
   - Different sources are considered (broker APIs, paid data vendors, exchange feeds, etc.).  
   - **Yahoo Finance** is selected as a practical choice due to its **free, widely used, and stable historical data** interface.

4. **Defining the dataset schema and scope**  
   - The minimal but standard OHLCV schema is chosen (`Date`, `Open`, `High`, `Low`, `Close`, `Volume`) to keep the dataset **simple, interoperable, and familiar**.  
   - The time range is set to cover **multiple economic cycles** (from 2000 to 2026), offering enough variety for robust analysis.

5. **Data collection from the chosen source**  
   - Using Yahoo Finance’s historical data tool, the full daily price history for INTC from 2000-01-03 to 2026-01-30 is downloaded as CSV.  
   - The raw file is inspected for completeness and consistency (no obvious missing trading days, correct ordering).

6. **Cleaning and structuring the data**  
   - Unnecessary columns (e.g., adjusted close if present) may be removed to simplify the dataset.  
   - Columns are reordered and standardized to match the final schema.  
   - Basic validation is performed (e.g., price relationships, non-negative volume).

7. **Documenting metadata, coverage, and provenance**  
   - Detailed explanations of each column, the temporal and geospatial scope, and the source (Yahoo Finance) are written.  
   - This documentation is compiled into this `app.md` file to make the dataset **self-describing and reusable**.

8. **Preparing the dataset for Kaggle and other platforms**  
   - The CSV file (`INTC.csv`) and this documentation (`app.md`) are packaged as a Kaggle-ready dataset.  
   - SEO-optimized naming, tags, and descriptions are crafted to maximize discoverability.

9. **Supporting downstream modeling and research**  
   - With the dataset and documentation in place, users can now:  
     - Build and benchmark predictive models.  
     - Study volatility, drawdowns, and risk measures.  
     - Combine INTC data with other external datasets (macroeconomic indicators, sector ETFs, etc.).

10. **Iterative improvement and maintenance**  
   - Over time, the dataset can be refreshed with new daily data and extended with derived features (returns, technical indicators, rolling statistics).  
   - Feedback from Kaggle users and researchers can guide further enhancements, such as adding benchmarks, peer stocks, or alternative frequencies.

This step-by-step development shows how an initial high-level question (“How has INTC behaved over time, and can we model it?”) leads to a precise, well-scoped dataset and project that is ready for analysis and machine learning.

