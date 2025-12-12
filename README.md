# 🎯 Algo Trading Signal Bot

**Professional-grade algorithmic trading system inspired by competition-winning strategies**

---

## 📖 Overview

This project builds a sophisticated trading signal bot that combines:
- **ICT (Inner Circle Trader)** strategy concepts
- **Mean Reversion** statistical approaches
- **Ensemble methodology** from competition winners (Optiver 2021)

**Key Features:**
- 50+ engineered features for market analysis
- Machine learning-inspired market regime detection
- Session-based trading (London + NY kill zones only)
- Futures-specific: MES, MNQ, MGC (micro contracts)
- Rigorous backtesting with walk-forward validation
- TradingView Pine Script indicators for live signals
- Prop firm compliant (3% per trade, 5% daily, 10% overall)

---

## 🚀 Quick Start

### Prerequisites
- Python 3.9+ (currently using 3.12.11)
- TradingView account (for Pine Script indicators + futures data)
- cTrader account via FundedHive (prop firm trading)
- Understanding of futures trading (MES, MNQ, MGC)

### Installation

```bash
# 1. Clone/Navigate to project
cd "/Users/jc/Desktop/algo trading/pinescript"

# 2. Create virtual environment
python3 -m venv venv

# 3. Activate virtual environment
source venv/bin/activate

# 4. Install all dependencies
pip install -r requirements.txt

# 5. Verify installation
python -c "import pandas, backtrader; print('✅ Ready to go!')"
```

### Daily Usage

```bash
# Activate virtual environment
source venv/bin/activate

# Run main script (once developed)
python main.py

# Deactivate when done
deactivate
```

---

## 📂 Project Structure

```
pinescript/
├── data_fetchers/          # Historical data downloading
├── features/               # Feature engineering (50+ features)
├── market_classifier/      # Market regime detection
├── strategies/             # ICT + Mean Reversion strategies
├── backtesting/            # Backtrader framework
├── indicators/             # Pine Script files for TradingView
├── data/                   # Historical price data (CSV)
├── results/                # Backtest results & reports
├── utils/                  # Utilities & helpers
├── config.yaml             # Configuration settings
├── requirements.txt        # Python dependencies
├── PROJECT_PLAN.md         # 📋 Complete project plan
└── main.py                 # Entry point
```

---

## 📊 Current Status

**Project Start:** December 12, 2024  
**Current Phase:** Week 1 - Foundation  
**Progress:** 0.6% (1/160 hours)  
**Next Milestone:** Data fetching system  

**Completed:**
- ✅ Environment setup
- ✅ Virtual environment created
- ✅ All packages installed (63 packages)
- ✅ Master project plan documented

**In Progress:**
- 🔄 Project folder structure
- 🔄 Data fetching system
- 🔄 Feature engineering framework

**Upcoming:**
- 📋 ICT strategy implementation
- 📋 Mean reversion strategy
- 📋 Ensemble optimization
- 📋 Pine Script indicators

---

## 🎓 Strategy Overview

### Two-Track System

1. **Python Track** (Development & Research)
   - Build and test strategies
   - Extract 50+ features
   - Backtest rigorously
   - Optimize parameters
   - **Output:** Optimal settings for Pine Script

2. **Pine Script Track** (Live Trading)
   - Display signals on TradingView
   - Visual order blocks, FVG zones
   - ATR-based stop loss/take profit
   - Real-time market regime display
   - **Output:** Actionable trading signals

3. **Manual Execution**
   - See signals on TradingView
   - Make final trading decision
   - Execute on cTrader (prop firm)
   - Track performance

### Strategy Components

**ICT Strategy (Trend-Following):**
- Order Blocks detection
- Fair Value Gaps (FVG)
- Liquidity Sweeps
- Market Structure (BOS/CHoCH)
- Session-based analysis

**Mean Reversion Strategy (Counter-Trend):**
- RSI extremes with divergence
- Bollinger Band touches
- Z-score analysis
- Volume confirmation

**Ensemble Logic:**
- Market regime detection (Trending vs Ranging)
- Adaptive weighting based on conditions
- Confidence scoring (0-100)
- Only trade high-confidence setups (>70)
- Session filters (London + NY kill zones only)

### Trading Setup (Futures-Specific)

**Instruments (Micro Futures):**
```
MES (Micro E-mini S&P 500) - 40% Weight
├─ Contract Value: $5 per point
├─ Typical ATR: 30 points
├─ Typical Stop: 60 points = $300 per contract
└─ Best for: Stable trends, ICT setups

MNQ (Micro NASDAQ-100) - 30% Weight
├─ Contract Value: $2 per point
├─ Typical ATR: 50 points
├─ Typical Stop: 100 points = $200 per contract
└─ Best for: High volatility, tech sector

MGC (Micro Gold) - 30% Weight
├─ Contract Value: $1 per point (10 oz)
├─ Typical ATR: $20
├─ Typical Stop: $40 = $40 per contract
└─ Best for: Diversification, safe-haven
```

**Account & Risk:**
```
Account Size: $50,000 (FundedHive)
Profit Split: 80% to trader when funded

Risk Limits (Prop Firm):
├─ Per Trade: 3% max = $1,500 (we use 1-2%)
├─ Daily: 5% max = $2,500 (we stop at 4%)
└─ Overall: 10% max = $5,000 drawdown

Conservative Approach:
├─ Typical Risk: 1% = $500 per trade
├─ Moderate Risk: 1.5% = $750 per trade
└─ Maximum Risk: 2% = $1,000 per trade
```

**Trading Sessions (Kill Zones ONLY):**
```
LONDON: 2:00 AM - 5:00 AM EST
├─ European open volatility
├─ Asian liquidity sweeps
├─ Conservative: 1% risk per trade
└─ All instruments active

NEW YORK: 7:00 AM - 10:00 AM EST (PRIMARY)
├─ US market open (highest volume)
├─ NY liquidity sweeps
├─ Moderate: 1-1.5% risk per trade
└─ Focus on MES/MNQ

⚠️ NO TRADING OUTSIDE KILL ZONES
```

---

## 📈 Performance Targets

**Backtesting Targets:**
- Sharpe Ratio: > 2.0
- Win Rate: 48-55%
- Profit Factor: > 1.5
- Max Drawdown: < 20%

**Live Trading Goals:**
- Risk per trade: 1-2% of account
- Risk/Reward: Minimum 1.5:1
- Monthly profitability
- Consistent execution

---

## 🛠️ Technologies Used

**Python Packages:**
- `pandas` (2.3.3) - Data manipulation
- `numpy` (2.2.6) - Numerical computing
- `backtrader` (1.9.78.123) - Backtesting framework
- `yfinance` (0.2.66) - Market data
- `scikit-learn` (1.8.0) - ML/Clustering
- `matplotlib` (3.10.8) - Visualization
- `streamlit` (1.52.1) - Dashboard (optional)

**Data Sources:**
- Yahoo Finance (yfinance) - Free, stocks/crypto/major forex
- Oanda API - Free practice account, all forex pairs
- MetaTrader 4/5 - Optional broker data

**Trading Platforms:**
- TradingView - Signal display
- cTrader - Trade execution (prop firm)

---

## 📚 Documentation

**Main Documents:**
- [PROJECT_PLAN.md](PROJECT_PLAN.md) - Complete project plan (READ THIS FIRST!)
- [requirements.txt](requirements.txt) - Python dependencies
- config.yaml - Configuration settings (to be created)

**Key Sections in PROJECT_PLAN.md:**
1. Executive Summary
2. Strategy Design (ICT + Mean Reversion)
3. Technical Architecture
4. 8-Week Development Timeline
5. Success Criteria
6. References (Competition winners)

---

## 🎯 Development Timeline

**Week 1:** Foundation + Data + Features (Current)  
**Week 2:** Feature Engineering Complete  
**Week 3:** ICT Strategy Implementation  
**Week 4:** Mean Reversion + Classifier  
**Week 5:** Ensemble + Optimization  
**Week 6-7:** Pine Script Indicators  
**Week 8:** Testing & Go Live  

**Total Time:** 8 weeks (160 hours @ 20 hrs/week)  
**Target Go-Live:** February 10-16, 2025  

---

## 🔍 References

**Inspired by Competition Winners:**

1. **Optiver Realized Volatility Prediction (2021) - 1st Place**
   - Ensemble: LightGBM + CNN + MLP
   - Feature engineering: 150+ features
   - Market clustering (K-means)
   - GPU-accelerated optimization

2. **Quantiacs - Dr. Kodiak (Multiple Wins)**
   - Real money: $2.5M portfolio managed
   - ATR-based risk management
   - Momentum + trend following
   - Profit sharing: $40K+/quarter

**GitHub Repositories Referenced:**
- [michaelpoluektov/orvp](https://github.com/michaelpoluektov/orvp) - Optiver 7th place
- [JSteveT/algorithmic-trading-strategies](https://github.com/JSteveT/algorithmic-trading-strategies)
- [FranklineMisango/Lumibot_Algorithms](https://github.com/FranklineMisango/Lumibot_Algorithms)

---

## ⚠️ Disclaimer

This is a personal trading project for educational and research purposes.

**Important Notes:**
- Past performance does not guarantee future results
- Trading involves substantial risk of loss
- Always use proper risk management
- Start with paper trading to validate
- Never risk more than you can afford to lose
- This is not financial advice

**For Prop Firm Trading:**
- Follow your prop firm's rules strictly
- Understand drawdown limits
- Practice proper position sizing
- Keep detailed trade journals

---

## 📝 License

Personal project - All rights reserved

---

## 👤 Author

**JC**  
Project: Algo Trading Signal Bot  
Start Date: December 12, 2024  

---

## 🤝 Contributing

This is a personal learning project. However, feedback and suggestions are welcome!

---

## 📞 Support

For questions about the project structure or implementation:
1. Check [PROJECT_PLAN.md](PROJECT_PLAN.md) first
2. Review code comments and docstrings
3. Consult referenced competition solutions

---

## 🎉 Acknowledgments

Special thanks to:
- Optiver competition winners for methodology inspiration
- Quantiacs platform and Dr. Kodiak for real-world validation
- Open-source community (pandas, backtrader, scikit-learn)
- TradingView for Pine Script platform
- GitHub repositories that provided learning examples

---

**Status:** 🔄 In Active Development  
**Last Updated:** December 12, 2024  
**Next Review:** End of Week 1 (December 22, 2024)  

---

## 🚀 Let's Build Something Great!

*"The goal is not to predict the future, but to find an edge in the present."*

Happy Trading! 📈
