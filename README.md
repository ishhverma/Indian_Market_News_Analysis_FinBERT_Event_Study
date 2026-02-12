# 📌 Indian Market News Analysis (FinBERT + Event Study)
This repository contains an end-to-end workflow for analyzing Indian market news using **NLP, FinBERT sentiment analysis, synthetic market data generation, event studies, and volatility impact analysis**.
The goal is to uncover actionable signals for **High-Frequency Trading (HFT)** and **Quantitative Finance** strategies.

# 🚀 Strategy & Approach (From Start to End)
## 1️⃣ Strategy Overview
This project is designed to convert **news headlines and descriptions** into **quantitative trading signals** by:
1. Extracting **sentiment** from news using FinBERT
2. Measuring **price reaction** using event study
3. Measuring **volatility & liquidity impact**
4. Generating **actionable signals** for trading strategies

## 2️⃣ Why News Matters in Trading
News is a primary driver of market movements because it changes:
* Investor expectations
* Future cash flows
* Risk perceptions
* Market sentiment
Therefore, capturing the **impact of news** can help build strategies for:
* **Momentum trading**
* **Event-driven trading**
* **Volatility trading**
* **News-based HFT signals**
# 🧠 Detailed Workflow (End-to-End)

## Step 1: Data Loading & Inspection
### Input Data
Two datasets are loaded:
| File                                 | Articles |
| ------------------------------------ | -------- |
| `indian_market_news_newsdata_io.csv` | 297      |
| `news_data.csv`                      | 100      |
### Outcome
Main analysis uses **297 news articles**.

## Step 2: Text Preprocessing & Named Entity Recognition (NER)
### Process
* Lowercase conversion
* Remove punctuation
* Remove stopwords
* Lemmatization
### NER Extraction
Using **spaCy** to identify:
* Organization (ORG)
* Person (PERSON)
* Geopolitical Entities (GPE)
* Money, Date, etc.
### Outcome
Cleaned text and entity extraction ready for sentiment analysis.

## Step 3: FinBERT Sentiment Analysis
### Model
`ProsusAI/finbert` — optimized for financial news sentiment.
### Process
* Combine cleaned title + description
* Classify into **Positive / Neutral / Negative**
### Results Summary (297 articles)
| Sentiment | Count | %     | Avg Confidence |
| --------- | ----- | ----- | -------------- |
| Positive  | 115   | 38.7% | 83.4%          |
| Neutral   | 144   | 48.5% | 79.8%          |
| Negative  | 38    | 12.8% | 77.0%          |
### Overall Sentiment Score
**+0.26 (Bullish)**
### Output Files
* `finbert_sentiment_analysis_results_<timestamp>.csv`
* `finbert_sentiment_summary_<timestamp>.json`
* `finbert_sentiment_analysis_report_<timestamp>.txt`

## Step 4: Synthetic Market Data Generation
### Why Synthetic Data?
Actual market data may not be available or may be restricted.
Synthetic data helps simulate:
* Price movement
* Volume
* Volatility metrics
### Generated Data
Date range: **2026-01-30 to 2026-02-20** (22 days)
Metrics:
* Open / Close / High / Low
* ATR
* Volume
* Implied Volatility

## Step 5: Event Study (Abnormal Returns)
### Objective
Measure average market return around news events.
### Event Window
**[-3, -2, -1, 0, +1, +2, +3]**
### Results
| Day | Avg Daily Return |
| --- | ---------------- |
| -3  | -0.29%           |
| -2  | -0.40%           |
| -1  | +0.06%           |
| 0   | +0.10%           |
| +1  | -0.20%           |
| +2  | **+0.56%**       |
| +3  | -0.04%           |
### Key Insight
📌 **Strong market reaction on Day +2**
This suggests a **delayed price discovery**, which can be exploited by event-driven strategies.

## Step 6: Volatility & Liquidity Impact Analysis
### Metrics
* ATR (Average True Range)
* Volume
* Implied Volatility (IV)
### Results
| Day | ATR Change | Volume Change | IV Change  |
| --- | ---------- | ------------- | ---------- |
| -3  | 0.00       | +1,825,075    | -0.214     |
| -2  | 0.00       | -644,149      | -0.011     |
| -1  | 0.00       | -153,974      | +0.091     |
| 0   | 0.00       | -157,975      | +0.003     |
| +1  | 0.00       | -559,877      | -0.076     |
| +2  | 0.00       | +428,273      | -0.052     |
| +3  | **-0.25**  | +575,655      | **+0.195** |

### Key Insights
📌 Volume and IV spikes indicate **higher market activity** and **price discovery**.
# 🧩 Trading Signals & Strategy Ideas
## Signal 1: Sentiment Momentum
If **FinBERT score is strongly positive**, consider:
* Long positions
* Momentum trading

## Signal 2: Event Reaction Window
Strong average return on **Day +2** suggests:
* Enter position near event day
* Exit on Day +2

## Signal 3: Volatility Breakout
If **IV rises sharply**, expect:
* Higher price swings
* Breakout opportunities
* Use options strategies or volatility trading

# 📊 Visualization & Dashboard
A multi-panel dashboard is generated:
* Sentiment distribution
* Top positive & negative news
* Event study chart
* Volatility & volume impact charts
https://www.canva.com/design/DAHADV3RxdI/xMTdAdutJ6JLGgFzg-CG2g/edit

# 🧾 Reports Generated
* `hft_quant_finance_report_<timestamp>.txt`

# 📌 How News Impacts the Market (Summary)
### News → Sentiment → Price → Volatility
* **Positive news** → bullish sentiment → price increase
* **Negative news** → bearish sentiment → price decrease
* **Neutral news** → minimal immediate impact
* **High-impact news** → volatility & volume spikes

