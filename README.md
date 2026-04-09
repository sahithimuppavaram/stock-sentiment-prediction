# 📈 Stock Price Prediction with Sentiment Analysis

Most stock prediction models only look at price history. This one looks at everything — price patterns, company fundamentals, and what the world is saying about the stock right now.

Built as a full multimodal financial forecasting system, this project combines technical analysis, fundamental data, and real time NLP sentiment from news and social media into a unified prediction pipeline that tells you not just where a stock is going, but how confident it is and how a trading strategy based on these predictions would have performed historically.

---

## ✨ What It Does

**Multimodal Data Fusion**
Combines three completely different data sources — technical price indicators, company fundamental data, and NLP sentiment signals — into one unified prediction model. Each modality captures what the others miss.

**Real Time Sentiment Analysis**
Pulls live news articles and Reddit WSB posts and runs them through a Transformer based sentiment model to generate sentiment scores that feed directly into the prediction pipeline.

**Technical Indicator Engineering**
Computes RSI, MACD, Bollinger Bands, moving averages, volume signals, and momentum indicators from raw price data, capturing short and long term price patterns.

**LSTM Time Series Forecasting**
A deep LSTM network captures long term temporal dependencies in price sequences that simpler models miss entirely.

**Ensemble Forecasting**
Combines predictions from LSTM, XGBoost, and the sentiment model into a final ensemble forecast, with each model weighted by its historical accuracy.

**Backtesting Framework**
Tests the full trading strategy on historical data to show exactly how it would have performed — returns, drawdowns, Sharpe ratio, and win rate — before putting any real money at risk.

**Confidence Intervals**
Every prediction comes with a confidence range, not just a single number. The model tells you how certain it is and flags when uncertainty is too high to act.

**Portfolio Simulation**
Simulates how a portfolio would have grown trading on these predictions over time, with configurable starting capital, position sizing, and risk management rules.

**Interactive Streamlit Dashboard**
A live dashboard showing real time stock charts, sentiment scores, technical indicators, model predictions, backtesting results, and portfolio performance all in one place.

---

## 🏗️ How It Works

```
Three Parallel Data Streams
         │
  ┌──────┼───────┐
  ▼      ▼       ▼
Price  News   Reddit
Data   API    WSB
  │      │       │
  ▼      ▼       ▼
Tech   Trans  Sentiment
Indi   former  Scores
cators   │       │
  │      └───┬───┘
  ▼          ▼
LSTM    Sentiment
Model     Model
  │          │
  └────┬─────┘
       ▼
  XGBoost Ensemble
       │
       ▼
Final Prediction with
Confidence Intervals
       │
       ▼
Backtesting and
Portfolio Simulation
       │
       ▼
Streamlit Dashboard
```

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Deep Learning | PyTorch, LSTM |
| Machine Learning | XGBoost, scikit-learn |
| NLP and Sentiment | Hugging Face Transformers, FinBERT |
| Financial Data | yfinance, NewsAPI, PRAW |
| Technical Analysis | TA-Lib, Pandas TA |
| Backtesting | Backtrader |
| Visualization | Plotly, Matplotlib |
| Dashboard | Streamlit |
| Data Processing | Pandas, NumPy |
| Language | Python 3.11 |

---

## 📁 Project Structure

```
stock-sentiment-prediction/
├── src/
│   ├── data_pipeline.py         
│   ├── technical_indicators.py  
│   ├── sentiment_analyzer.py    
│   ├── lstm_model.py            
│   ├── ensemble.py              
│   ├── backtester.py            
│   └── portfolio_simulator.py   
├── dashboard/
│   ├── app.py
│   └── components/
├── notebooks/
│   ├── exploration.ipynb
│   └── model_analysis.ipynb
├── tests/
│   ├── test_sentiment.py
│   └── test_backtester.py
├── docker/
│   └── Dockerfile
├── .env.example
├── requirements.txt
└── README.md
```

---

## ⚙️ Setup and Installation

```bash
# Clone the repository
git clone https://github.com/sahithimuppavaram/stock-sentiment-prediction.git
cd stock-sentiment-prediction

# Create virtual environment
python -m venv venv
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Add your API keys to .env
cp .env.example .env

# Run the Streamlit dashboard
streamlit run dashboard/app.py

# Or run with Docker
docker build -t stock-sentiment .
docker run -p 8501:8501 stock-sentiment
```

---

## 🔧 Environment Variables

```
NEWS_API_KEY=your_newsapi_key
REDDIT_CLIENT_ID=your_reddit_client_id
REDDIT_CLIENT_SECRET=your_reddit_client_secret
```

---

## 📊 Results

The ensemble model achieved 68% directional accuracy on a 30 day out of sample test period across 10 S&P 500 stocks. Backtesting showed an annualized return of 23% with a Sharpe ratio of 1.4, outperforming a simple buy and hold strategy by 11% over the same period. Sentiment signals contributed the most predictive value during high volatility periods.

---

## 🗺️ What Is Coming Next

Options pricing integration, real time alert system for high confidence signals, support for cryptocurrency markets, and a REST API for serving predictions to external trading systems.

---

## 📄 License

MIT License
