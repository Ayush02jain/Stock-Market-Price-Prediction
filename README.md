# 📈 Stock Market Price Prediction

A backend system that analyzes historical stock market data and predicts future prices using LSTM neural networks. Built to help retail investors make informed decisions without expensive analytical tools.

---

## 🎯 Problem Statement

Stock prices are volatile and notoriously difficult to predict manually. Most retail investors lack access to sophisticated prediction tools. This project bridges that gap by providing an API-driven backend that processes historical data and generates price predictions with reasonable accuracy.

---

## ✨ Features

- **Real-time Data Fetching**: Pulls historical stock data via Yahoo Finance API
- **Smart Preprocessing**: Handles missing values, normalizes prices, and prevents data leakage
- **Feature Engineering**: Generates technical indicators (Moving Averages, RSI)
- **LSTM Prediction Model**: Deep learning model that captures temporal patterns
- **REST API**: Easy-to-consume endpoints for any frontend or third-party integration
- **Visualization**: Model performance tracking during development

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| **Language** | Python |
| **Data Processing** | Pandas, NumPy |
| **Machine Learning** | Scikit-learn, Keras (TensorFlow) |
| **Model Architecture** | LSTM (Long Short-Term Memory) |
| **API Framework** | Flask |
| **Data Source** | Yahoo Finance API (yfinance) |
| **Visualization** | Matplotlib |

---

## 📁 Project Structure

```
stock-price-prediction/
│
├── app.py                  # Flask API server
├── train_model.py          # Model training script
├── data/
│   ├── fetch_data.py       # Yahoo Finance data fetching
│   └── preprocess.py       # Data cleaning & feature engineering
├── models/
│   ├── lstm_model.py       # LSTM architecture
│   └── saved_models/       # Trained model checkpoints
├── utils/
│   ├── feature_engineering.py
│   └── visualization.py
├── requirements.txt
└── README.md
```

---

## 🧠 How It Works

1. **Data Collection**: Fetches historical stock prices from Yahoo Finance
2. **Preprocessing**: 
   - Handles missing values
   - Chronological train/test split (prevents data leakage)
   - Normalization fitted *only* on training data
3. **Feature Engineering**: Calculates moving averages (MA), RSI, volatility indicators
4. **Model Training**: LSTM network learns temporal patterns from sequential data
5. **Prediction**: Generates future price predictions
6. **API Serving**: Flask exposes predictions via REST endpoints

---

## 🎓 Key Lessons Learned

### The Data Leakage Problem
Initially achieved 95%+ accuracy — which seemed amazing until I realized the model had accidentally seen future data during preprocessing. 

**The Fix:**
- Split data chronologically *before* any transformation
- Fit scalers only on training data
- Apply same transformation to test data
- Real accuracy: ~78% (but trustworthy)

**Takeaway:** In time-series problems, the order of operations in your pipeline is just as critical as the model itself. A model that looks too good usually *is* too good.

---

## 🔮 Future Improvements

- [ ] Add sentiment analysis from news/social media
- [ ] Support multiple prediction models (ensemble approach)
- [ ] Implement real-time WebSocket updates
- [ ] Add user authentication and portfolio tracking
- [ ] Deploy on cloud (AWS/GCP)
- [ ] Containerize with Docker

---

## ⚠️ Disclaimer

This project is for educational purposes only. Stock market prediction is inherently uncertain. Do not use these predictions as the sole basis for investment decisions. Always consult with a financial advisor.

---

## 🙏 Acknowledgments

- Yahoo Finance for providing free historical stock data
- TensorFlow/Keras community for LSTM implementation guidance
- The lesson that "too good to be true" metrics usually are
