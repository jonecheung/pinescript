# 🎯 Algo Trading Signal Bot - Master Project Plan

**Project Start Date:** December 12, 2024  
**Expected Completion:** February 10, 2025 (8 weeks)  
**Developer:** JC  
**Time Commitment:** 20 hours/week  

---

## 📋 Executive Summary

### Project Goal
Build a professional-grade algorithmic trading signal bot using ensemble strategies (ICT + Mean Reversion) inspired by competition-winning approaches, specifically the Optiver Realized Volatility Prediction competition winner's methodology.

### Key Approach
- **Two-Track System**: Python for research/backtesting, Pine Script for live signal display
- **Ensemble Strategy**: Combine ICT (Inner Circle Trader) concepts with Mean Reversion
- **Optiver-Inspired**: Advanced feature engineering (50+ features), market regime detection, clustering
- **Manual Execution**: Signals displayed on TradingView, manually executed on cTrader (prop firm)

### Expected Outcome
A fully backtested trading system with:
- Sharpe Ratio > 2.0
- Win Rate: 45-55%
- Max Drawdown < 20%
- Profit Factor > 1.5

---

## 1. Project Overview

### 1.1 Objectives

**Primary Goal:**
- Develop a trading signal bot that generates high-quality buy/sell signals
- Display signals on TradingView for manual execution
- Achieve consistent, statistically validated edge

**Secondary Goals:**
- Learn professional algo trading development practices
- Understand competition-winning strategies
- Build reusable, maintainable codebase
- Create comprehensive backtesting framework

### 1.2 Trading Setup

**Broker & Platform:**
- Prop Firm: FundedHive using cTrader
- TradingView for signal display and chart analysis
- No automated execution (manual entry/exit)

**Instruments (Futures - Micro Contracts):**
- Primary Focus (70%):
  - MES (Micro E-mini S&P 500) - 40% weight
  - MNQ (Micro NASDAQ-100) - 30% weight
- Secondary (30%):
  - MGC (Micro Gold) - 30% weight
- Timeframes: H4 (bias), H1 (structure), M15 (entry)

**Trading Style:**
- Session-based: London Kill Zone (2-5 AM EST) + NY Kill Zone (7-10 AM EST)
- Hold times: Minutes to hours (no weekend holding when funded)
- Risk management: ATR-based stops, max 3% per trade, 5% daily limit

### 1.3 Key Requirements

**Must Have:**
✅ Rigorous backtesting (2+ years historical data)  
✅ Ensemble approach (multiple signal sources)  
✅ TradingView Pine Script indicators  
✅ Clear visual signals  
✅ ATR-based stop loss recommendations  
✅ Session-time filters (London + NY only)  
✅ Prop firm rule compliance (5% daily, 3% per trade)  
✅ Performance metrics tracking  

**Nice to Have:**
- Real-time Python signal monitor (optional)
- Multiple currency pair support
- Mobile notifications
- Trading journal integration

---

## 2. Strategy Design

### 2.1 Inspiration: Competition Winners

**Primary Reference: Optiver Realized Volatility Prediction (2021) - 1st Place**

**Winning Techniques Adopted:**
1. **Ensemble Models**: Combine multiple approaches (LightGBM + CNN + MLP → ICT + Mean Reversion)
2. **Feature Engineering**: Extract 50+ meaningful features from price/volume data
3. **Market Clustering**: K-means to identify similar market conditions
4. **Time-Series Patterns**: Temporal feature aggregation
5. **Rigorous Validation**: Walk-forward testing, out-of-sample validation

**Secondary Reference: Quantiacs (Dr. Kodiak) - Multiple Wins**

**Winning Techniques Adopted:**
1. **ATR-Based Risk Management**: Dynamic stops based on volatility
2. **Position Sizing**: Risk % of account / ATR distance
3. **Diversification**: Multiple uncorrelated instruments (MES, MNQ, Gold)
4. **Momentum Principles**: Trend-following bias
5. **Futures Focus**: Dr. Kodiak traded FUTURES - perfect alignment! ✅

### 2.2 ICT Strategy Components

**Core Concepts:**
- **Order Blocks**: High-volume institutional zones (support/resistance)
- **Fair Value Gaps (FVG)**: Imbalance zones where price moved too fast
- **Liquidity Sweeps**: Stop hunts before reversal
- **Market Structure**: Break of Structure (BOS), Change of Character (CHoCH)
- **Kill Zones**: Optimal trading times (London/New York sessions)
- **Premium/Discount**: Fibonacci 50% levels for entry timing

**Signal Generation:**
- Confluence of multiple ICT factors
- Weighted scoring system (0-100)
- Higher timeframe bias confirmation

**Entry Criteria:**
- Order block identified + FVG present + Liquidity swept
- Premium/discount zone alignment
- Session time confirmation (London 2-5 AM or NY 7-10 AM EST)
- Minimum confidence score: 70/100
- Within prop firm limits (max 3% risk per trade)

### 2.3 Mean Reversion Components

**Core Concepts:**
- **Bollinger Bands**: Price deviation from mean
- **RSI Divergence**: Price vs momentum divergence
- **Z-Score**: Statistical distance from mean
- **Volume Confirmation**: Above-average volume on reversal
- **Support/Resistance**: Historical price levels

**Signal Generation:**
- Oversold/overbought extremes
- Divergence detection
- Volume spike confirmation
- Weighted scoring system (0-100)

**Entry Criteria:**
- RSI < 30 (oversold) or > 70 (overbought)
- Price touching Bollinger Band
- Divergence present
- Volume confirmation
- Minimum confidence score: 70/100

### 2.4 Ensemble Approach

**Signal Combination Logic:**

```
Market Regime Detection:
├─ TRENDING (ADX > 25, high directional movement)
│  └─ Weight: ICT 70%, Mean Reversion 30%
│  └─ Best for: MES, MNQ (indices trend well)
│
├─ RANGING (ADX < 20, low directional movement)
│  └─ Weight: ICT 30%, Mean Reversion 70%
│  └─ Best for: Gold during consolidation
│
└─ UNCERTAIN (ADX 20-25)
   └─ Weight: ICT 50%, Mean Reversion 50%
   └─ Trade only in kill zones
```

**Final Signal Strength:**
- > 80: STRONG (high confidence)
- 70-80: MODERATE (good setup)
- 50-70: WEAK (low confidence, skip)
- < 50: NO TRADE

**Trade Execution:**
- Only take STRONG or MODERATE signals
- Require both strategies to show same direction
- Use higher timeframe for bias confirmation

---

## 3. Technical Architecture

### 3.1 Two-Track System

```
┌────────────────────────────────────────────────────┐
│  TRACK 1: PYTHON (Research & Development)          │
│  ─────────────────────────────────────────────     │
│  Role: Strategy development, backtesting           │
│  Runs: Offline, on your laptop                    │
│  Frequency: Monthly updates (1-2 hrs/month)       │
│  Output: Optimized parameters for Pine Script     │
└────────────────────────────────────────────────────┘
                        ↓
              Transfer findings to...
                        ↓
┌────────────────────────────────────────────────────┐
│  TRACK 2: PINE SCRIPT (Production Trading)         │
│  ─────────────────────────────────────────────     │
│  Role: Live signal generation on TradingView       │
│  Runs: 24/7 on TradingView servers                │
│  Frequency: Real-time, always active              │
│  Output: Visual signals on charts                 │
└────────────────────────────────────────────────────┘
                        ↓
                You see signals
                        ↓
┌────────────────────────────────────────────────────┐
│  TRACK 3: MANUAL TRADING (Execution)               │
│  ─────────────────────────────────────────────     │
│  Role: Execute trades on cTrader                   │
│  Runs: When signals appear                        │
│  You: Make final decision and place trades        │
└────────────────────────────────────────────────────┘
```

### 3.2 Python Components

**Project Structure:**
```
pinescript/
├── data_fetchers/          # Historical data downloading
│   ├── yfinance_fetcher.py
│   ├── oanda_fetcher.py
│   └── data_manager.py
│
├── features/               # Feature engineering (50+ features)
│   ├── price_features.py
│   ├── volume_features.py
│   ├── volatility_features.py
│   ├── ict_features.py
│   ├── mean_reversion_features.py
│   └── feature_manager.py
│
├── market_classifier/      # Market regime detection
│   ├── regime_detector.py
│   └── pattern_clustering.py
│
├── strategies/             # Strategy implementations
│   ├── base_strategy.py
│   ├── ict_strategy.py
│   ├── mean_reversion_strategy.py
│   └── ensemble_strategy.py
│
├── backtesting/            # Backtesting framework
│   ├── backtrader_engine.py
│   ├── data_loader.py
│   ├── performance_analyzer.py
│   └── walk_forward.py
│
├── utils/                  # Utilities
│   ├── config.py
│   ├── helpers.py
│   └── logger.py
│
├── data/                   # Historical price data (CSV)
├── results/                # Backtest results
├── config.yaml             # Configuration
├── requirements.txt        # Python packages
└── main.py                 # Entry point
```

**Key Technologies:**
- **Data**: pandas, numpy, yfinance
- **Backtesting**: backtrader
- **ML/Optimization**: scikit-learn (K-means, clustering)
- **Visualization**: matplotlib, plotly, seaborn
- **GUI** (optional): streamlit

### 3.3 Pine Script Components

**Indicators to Build:**
```
indicators/
├── ict_signals.pine           # ICT strategy indicator
│   ├── Order blocks detection
│   ├── Fair Value Gaps
│   ├── Liquidity sweeps
│   └── Market structure
│
├── mean_reversion.pine        # Mean reversion indicator
│   ├── RSI + Bollinger Bands
│   ├── Divergence detection
│   └── Volume confirmation
│
├── ensemble_dashboard.pine    # Combined signals
│   ├── Signal strength display
│   ├── Market regime indicator
│   ├── Confidence scores
│   └── Trade statistics
│
└── risk_levels.pine           # ATR-based levels
    ├── Stop loss lines
    ├── Take profit zones
    └── Risk/reward display
```

### 3.4 Futures Instruments Specifications

**MES (Micro E-mini S&P 500) - 40% Weight**
- TradingView Symbol: `MES1!` or `ES=F` (yfinance)
- Contract Value: $5 per point
- Tick Size: 0.25 points = $1.25
- Typical ATR: 30 points
- Typical Stop: 60 points (2×ATR) = $300 risk per contract
- Trading Hours: Nearly 24hr (Sun 6PM - Fri 5PM EST)
- **Why Primary**: Most liquid, stable trends, perfect for ICT

**MNQ (Micro NASDAQ-100) - 30% Weight**
- TradingView Symbol: `MNQ1!` or `NQ=F` (yfinance)
- Contract Value: $2 per point
- Tick Size: 0.25 points = $0.50
- Typical ATR: 50 points
- Typical Stop: 100 points (2×ATR) = $200 risk per contract
- Trading Hours: Nearly 24hr (Sun 6PM - Fri 5PM EST)
- **Why Primary**: High volatility, strong trends, tech-focused

**MGC (Micro Gold) - 30% Weight**
- TradingView Symbol: `MGC1!` or `GC=F` (yfinance)
- Contract Value: $1 per point (10 troy oz)
- Tick Size: $0.10 = $0.10
- Typical ATR: $20
- Typical Stop: $40 (2×ATR) = $40 risk per contract
- Trading Hours: Nearly 24hr (Sun 6PM - Fri 5PM EST)
- **Why Secondary**: Diversification, safe-haven, different driver

**Session Times (Kill Zones):**
```
LONDON KILL ZONE: 2:00 AM - 5:00 AM EST
├─ European open volatility
├─ Liquidity sweeps from Asian session
├─ All instruments active
└─ Conservative risk (1% per trade)

NEW YORK KILL ZONE: 7:00 AM - 10:00 AM EST
├─ US open volatility (HIGHEST)
├─ Liquidity sweeps from overnight
├─ Focus on MES/MNQ (US indices)
└─ Moderate risk (1-1.5% per trade)

NO TRADING OUTSIDE KILL ZONES
(Exception: Major news events, strong trend continuation)
```

### 3.5 Data Flow

```
Historical Data Sources (FUTURES)
├─ yfinance: ES=F, NQ=F, GC=F (free, 2+ years)
├─ TradingView: MES1!, MNQ1!, MGC1! (premium data)
└─ CTrader historical export (optional, broker data)
        ↓
    Download & Store
        ↓
CSV Files in data/ folder
(MES_M15.csv, MNQ_H1.csv, MGC_H4.csv)
        ↓
    Python Processing
        ↓
Feature Extraction (50+ features)
+ Session Time Filters (London/NY only)
        ↓
Strategy Backtesting
        ↓
Parameter Optimization
        ↓
Optimal Settings Identified
        ↓
    Transfer to Pine Script
        ↓
TradingView Indicators (MES1!, MNQ1!, MGC1!)
        ↓
Live Chart Signals (during kill zones only)
        ↓
Manual Trading Execution on cTrader
        ↓
Check Prop Firm Limits Before Each Trade
```

---

## 4. Timeline & Resources

### 4.1 Project Duration

**Total Time:** 8 weeks (2 months)  
**Start Date:** Week of December 16, 2024  
**Target Go-Live:** Week of February 10, 2025  

**Buffer:** +1 week for holidays/unexpected issues  
**Realistic Go-Live:** Mid-February 2025  

### 4.2 Time Investment

**Weekly Commitment:** 20 hours  
**Total Hours:** 160 hours  

**Distribution:**
- Python Development: 75 hours (47%)
- Pine Script: 37 hours (23%)
- Testing & Validation: 30 hours (19%)
- Documentation: 18 hours (11%)

**Daily Schedule Example:**
- Monday: 4 hours (7-11 PM)
- Wednesday: 4 hours (7-11 PM)
- Friday: 4 hours (7-11 PM)
- Saturday: 4 hours (9 AM-1 PM)
- Sunday: 4 hours (2-6 PM)

### 4.3 Weekly Breakdown

| Week | Focus | Hours | Deliverables |
|------|-------|-------|--------------|
| 1 | Foundation + Data + Features | 20 | Data system, 50+ features ✅ |
| 2 | Feature Engineering Complete | 20 | All features tested |
| 3 | ICT Strategy | 20 | Order blocks, FVG, structure |
| 4 | Mean Reversion + Classifier | 20 | MR strategy, regime detection |
| 5 | Ensemble + Optimization | 20 | Combined strategy, optimized |
| 6 | Pine Script Part 1 | 20 | ICT + MR indicators |
| 7 | Pine Script Part 2 | 20 | Ensemble dashboard, polish |
| 8 | Testing & Documentation | 20 | Final validation, docs |

---

## 5. Detailed Development Plan

### Week 1: Foundation + Data + Features (20 hours)

**Goals:**
- ✅ Set up project structure
- ✅ Build data fetching system
- ✅ Extract 50+ features from price data

**Tasks:**
1. **Project Structure (10 minutes)** ✅
   - Create all folders
   - Set up __init__.py files
   - Configure .gitignore

2. **Data Fetching System (3 hours)**
   - Build yfinance fetcher
   - Build Oanda API fetcher
   - Test downloading EURUSD, GBPUSD (2 years)
   - Verify data quality

3. **Feature Engineering (5 hours)**
   - Price features (20 features)
   - Volume features (10 features)
   - Volatility features (10 features)
   - ICT features (10 features)
   - Mean reversion features (10 features)
   - Test extraction on sample data

4. **Data Loader for Backtrader (2 hours)**
   - Convert CSV to Backtrader format
   - Handle multiple timeframes
   - Test loading M15, H1, H4 simultaneously

**Deliverables:**
- ✅ Complete project structure
- ✅ Working data downloaders
- ✅ 50+ features extracted
- ✅ Data ready for backtesting

**Progress:** ~12% of project complete

---

### Week 2: Feature Engineering Complete (20 hours)

**Goals:**
- Complete and refine all feature extractors
- Add clustering and regime detection
- Validate feature quality

**Tasks:**
1. **ICT Feature Refinement (6 hours)**
   - Improve order block detection
   - Refine FVG identification
   - Add liquidity sweep detection
   - Test on multiple instruments

2. **Market Regime Detector (5 hours)**
   - ADX-based trend detection
   - Volatility regime classification
   - Build regime classifier

3. **Clustering System (4 hours)**
   - K-means clustering implementation
   - Find similar market conditions
   - Test cluster quality

4. **Feature Validation (5 hours)**
   - Statistical analysis of features
   - Correlation matrix
   - Feature importance ranking
   - Remove redundant features

**Deliverables:**
- ✅ All 50+ features refined and tested
- ✅ Market regime detector working
- ✅ Clustering system functional
- ✅ Feature quality validated

**Progress:** ~25% of project complete

---

### Week 3: ICT Strategy Implementation (20 hours)

**Goals:**
- Build complete ICT strategy in Python
- Implement in Backtrader
- Run initial backtests

**Tasks:**
1. **Order Block Strategy (5 hours)**
   - Detect bullish/bearish order blocks
   - Volume confirmation
   - Entry/exit logic

2. **Fair Value Gap Strategy (4 hours)**
   - Detect FVG zones
   - Entry on retest
   - Target zones

3. **Market Structure (5 hours)**
   - Break of Structure (BOS) detection
   - Change of Character (CHoCH)
   - Trend direction determination

4. **ICT Signal Scoring (3 hours)**
   - Combine all ICT components
   - Weighted scoring (0-100)
   - Threshold tuning

5. **Initial Backtesting (3 hours)**
   - Test ICT strategy standalone
   - Analyze performance
   - Identify issues

**Deliverables:**
- ✅ Complete ICT strategy
- ✅ Backtested on 2 years data
- ✅ Initial performance metrics
- ✅ Issues identified and documented

**Progress:** ~37% of project complete

---

### Week 4: Mean Reversion + Market Classifier (20 hours)

**Goals:**
- Build mean reversion strategy
- Integrate market classifier
- Compare strategies

**Tasks:**
1. **Mean Reversion Core (6 hours)**
   - RSI-based signals
   - Bollinger Band touches
   - Z-score extremes
   - Entry/exit logic

2. **Divergence Detection (4 hours)**
   - Price-RSI divergence
   - Volume divergence
   - Divergence strength scoring

3. **Mean Reversion Scoring (3 hours)**
   - Combine MR components
   - Weighted scoring (0-100)
   - Threshold tuning

4. **Strategy Comparison (4 hours)**
   - ICT vs Mean Reversion performance
   - Win rate, Sharpe ratio, drawdown
   - Best use cases for each

5. **Market Classifier Integration (3 hours)**
   - Detect trending vs ranging
   - Strategy selection logic
   - Test adaptive switching

**Deliverables:**
- ✅ Complete mean reversion strategy
- ✅ Divergence detection working
- ✅ Both strategies backtested
- ✅ Market classifier integrated

**Progress:** ~50% of project complete

---

### Week 5: Ensemble + Optimization (20 hours)

**Goals:**
- Combine ICT + Mean Reversion
- Optimize all parameters
- Walk-forward validation

**Tasks:**
1. **Ensemble Logic (5 hours)**
   - Signal combination algorithm
   - Weighted averaging by regime
   - Confidence threshold tuning

2. **Parameter Optimization (6 hours)**
   - Grid search optimal parameters
   - ATR multiplier (stop loss)
   - RSI thresholds
   - Bollinger Band settings
   - Order block criteria

3. **Walk-Forward Testing (5 hours)**
   - In-sample training
   - Out-of-sample testing
   - Rolling window validation
   - Prevent overfitting

4. **Performance Analysis (4 hours)**
   - Sharpe ratio calculation
   - Maximum drawdown
   - Win rate, profit factor
   - Trade distribution analysis
   - Generate reports

**Deliverables:**
- ✅ Ensemble strategy working
- ✅ Optimized parameters found
- ✅ Walk-forward validated
- ✅ Performance reports generated

**Progress:** ~62% of project complete

**Target Metrics:**
- Sharpe Ratio: > 2.0
- Win Rate: 48-55%
- Max Drawdown: < 20%
- Profit Factor: > 1.5

---

### Week 6: Pine Script Part 1 (20 hours)

**Goals:**
- Learn Pine Script basics
- Build ICT indicator
- Build mean reversion indicator

**Tasks:**
1. **Pine Script Learning (4 hours)**
   - Syntax and structure
   - Built-in functions
   - Technical analysis library
   - Plotting and labels

2. **ICT Indicator (8 hours)**
   - Order blocks visualization
   - Fair Value Gap zones
   - Liquidity sweep markers
   - Market structure lines
   - Signal labels on chart

3. **Mean Reversion Indicator (6 hours)**
   - RSI with divergence
   - Bollinger Bands overlay
   - Oversold/overbought markers
   - Signal labels

4. **Testing on TradingView (2 hours)**
   - Upload indicators
   - Test on multiple pairs
   - Verify signals match Python

**Deliverables:**
- ✅ ICT indicator on TradingView
- ✅ Mean reversion indicator
- ✅ Both tested and working
- ✅ Signals validated vs Python

**Progress:** ~75% of project complete

---

### Week 7: Pine Script Part 2 (20 hours)

**Goals:**
- Build ensemble dashboard
- Add ATR-based levels
- Visual polish and refinements

**Tasks:**
1. **Ensemble Dashboard (6 hours)**
   - Combined signal display
   - Confidence scores
   - Market regime indicator
   - Signal history table

2. **ATR-Based Levels (4 hours)**
   - Stop loss lines
   - Take profit zones
   - Risk/reward calculation
   - Position size suggestion

3. **Visual Refinements (5 hours)**
   - Color schemes
   - Label placement
   - Chart cleanliness
   - Mobile-friendly display

4. **Alert System (3 hours)**
   - Buy/sell alerts
   - Confidence level alerts
   - Custom alert messages

5. **Final Testing (2 hours)**
   - Test on 5+ currency pairs
   - Verify all features work
   - Mobile app testing

**Deliverables:**
- ✅ Complete ensemble indicator
- ✅ ATR-based risk levels
- ✅ Professional visual design
- ✅ Alert system functional

**Progress:** ~87% of project complete

---

### Week 8: Testing & Documentation (20 hours)

**Goals:**
- Final validation
- Comprehensive documentation
- Trading checklist
- Go live preparation

**Tasks:**
1. **Final Validation (6 hours)**
   - Compare Python vs Pine Script signals
   - Verify consistency
   - Test edge cases
   - Final parameter tweaks

2. **Documentation (8 hours)**
   - Strategy explanation
   - How to use indicators
   - Parameter meanings
   - Troubleshooting guide
   - FAQ

3. **Trading Checklist (3 hours)**
   - Pre-trade checklist
   - Signal confirmation steps
   - Risk management rules
   - Trade journaling template

4. **Performance Tracking Setup (3 hours)**
   - Excel/Google Sheets template
   - Metrics to track
   - Review process

**Deliverables:**
- ✅ All systems validated
- ✅ Complete documentation
- ✅ Trading checklist ready
- ✅ Performance tracking set up
- 🎉 READY TO GO LIVE!

**Progress:** 100% COMPLETE! 🚀

---

## 6. Progress Tracking

### ✅ Phase 1: Environment Setup (COMPLETED)

**Completed on:** December 12, 2024  
**Time Spent:** 1 hour  

**Achievements:**
- ✅ Python 3.12.11 installed
- ✅ Virtual environment created
- ✅ requirements.txt created
- ✅ 63 packages installed successfully
- ✅ All packages tested and working

**Key Packages Installed:**
- pandas 2.3.3
- numpy 2.2.6
- backtrader 1.9.78.123
- yfinance 0.2.66
- scikit-learn 1.8.0
- matplotlib 3.10.8
- streamlit 1.52.1

### 🔄 Phase 2: Foundation (CURRENT - Week 1)

**Status:** Ready to start  
**Estimated Time:** 10 hours  
**Target Completion:** December 22, 2024  

**Tasks:**
- [ ] Create project folder structure
- [ ] Build yfinance data fetcher
- [ ] Build Oanda data fetcher
- [ ] Download 2 years EURUSD, GBPUSD data
- [ ] Extract 50+ features
- [ ] Build Backtrader data loader
- [ ] Test feature extraction

### 📋 Phase 3: Strategy Development (Week 2-5)

**Status:** Upcoming  
**Estimated Time:** 80 hours  
**Target Completion:** January 26, 2025  

**Major Milestones:**
- [ ] All features refined (Week 2)
- [ ] ICT strategy complete (Week 3)
- [ ] Mean reversion complete (Week 4)
- [ ] Ensemble optimized (Week 5)

### 📋 Phase 4: Pine Script (Week 6-7)

**Status:** Upcoming  
**Estimated Time:** 40 hours  
**Target Completion:** February 9, 2025  

**Major Milestones:**
- [ ] ICT indicator on TradingView (Week 6)
- [ ] Mean reversion indicator (Week 6)
- [ ] Ensemble dashboard (Week 7)
- [ ] ATR-based levels (Week 7)

### 📋 Phase 5: Go Live (Week 8)

**Status:** Upcoming  
**Estimated Time:** 20 hours  
**Target Completion:** February 16, 2025  

**Major Milestones:**
- [ ] Final validation
- [ ] Documentation complete
- [ ] Trading checklist ready
- [ ] 🚀 START LIVE TRADING!

---

## 7. Success Criteria

### 7.1 Technical Metrics (Backtesting)

**Minimum Acceptable:**
- Sharpe Ratio: > 1.5
- Win Rate: > 45%
- Profit Factor: > 1.3
- Max Drawdown: < 25%

**Target (Good):**
- Sharpe Ratio: > 2.0 ✅
- Win Rate: 48-52%
- Profit Factor: > 1.5
- Max Drawdown: < 20%

**Stretch (Excellent):**
- Sharpe Ratio: > 2.5
- Win Rate: > 55%
- Profit Factor: > 2.0
- Max Drawdown: < 15%

### 7.2 System Quality

**Code Quality:**
- [ ] Clean, readable code
- [ ] Proper documentation
- [ ] Modular design
- [ ] Error handling
- [ ] Unit tests (optional)

**Backtesting Quality:**
- [ ] 2+ years historical data
- [ ] Multiple instruments tested
- [ ] Walk-forward validation
- [ ] Out-of-sample testing
- [ ] Realistic slippage/commissions

**Pine Script Quality:**
- [ ] Signals match Python
- [ ] Clean visual design
- [ ] Mobile-friendly
- [ ] Alert system working
- [ ] Performance optimized

### 7.3 Trading Performance (Live)

**First Month Goals:**
- Follow signals consistently
- Track all trades
- Learn signal quality patterns
- Refine execution

**First 3 Months Goals:**
- Positive expectancy
- Consistent with backtest
- < 15% drawdown
- Build confidence

**Long-Term Goals:**
- Monthly profitability
- Compounding growth
- Adapt to market changes
- Continuous improvement

---

## 8. Risk Management

### 8.1 Trading Risk (FundedHive Prop Firm Rules)

**Account Details:**
- Starting Capital: $50,000
- Scale up: After consistent profitability
- Platform: cTrader
- Instruments: Micro futures only (MES, MNQ, MGC)

**Prop Firm Hard Limits:**
- **Max Per-Trade Loss**: 3% = $1,500 (HARD LIMIT)
- **Max Daily Loss**: 5% = $2,500 (HARD LIMIT)  
- **Max Overall Drawdown**: 10% = $5,000 (HARD LIMIT)
- **Weekend Holding**: ❌ NOT allowed when funded
- **News Trading**: ✅ ALLOWED

**Our Conservative Approach:**
- **Typical**: 1% per trade = $500 risk
- **Moderate**: 1.5% per trade = $750 risk
- **Maximum**: 2% per trade = $1,000 risk (well below 3% limit)
- **Daily Risk Budget**: 4% = $2,000 (below 5% limit with buffer)

**ATR-Based Stops (Futures-Specific):**
- Stop Loss: Entry ± (ATR × 2.0) in points
- Take Profit: Entry ± (ATR × 3.0) in points
- Risk/Reward: Minimum 1.5:1

**Position Sizing Formula (Futures):**
```
Position Size = (Account × Risk%) / (Stop Distance × Contract Value)

Example MES:
$50,000 × 1% = $500 risk
60 points stop × $5/point = $300 per contract
$500 / $300 = 1.66 → 1 contract (conservative)
```

**Daily Limits:**
- Max trades: 2-3 per day
- Stop trading if: Lost 4% ($2,000) in one day
- Max open trades: 2 simultaneous

### 8.2 Development Risk

**Overfitting Prevention:**
- Walk-forward validation
- Out-of-sample testing
- Multiple market conditions
- Conservative parameter selection

**Reality Check:**
- Include realistic slippage
- Include commissions/spreads
- Account for execution delay
- Psychological factors

### 8.3 Psychological Risk

**Discipline:**
- Only trade signals > 70 confidence
- Never override stop loss
- Stick to position sizing
- Journal all trades

**Emotional Management:**
- Accept losses as part of system
- Don't chase trades
- Take breaks after drawdowns
- Review performance objectively

---

## 9. References & Resources

### 9.1 Competition Winners Studied

**Optiver Realized Volatility Prediction (2021) - 1st Place**
- Ensemble: LightGBM + 1D-CNN + MLP
- Feature Engineering: 150+ features
- t-SNE compression for time-series
- KNN for temporal patterns
- K-means for stock clustering
- GPU acceleration
- Reference: [Kaggle Discussion](https://zizouhe.github.io/reading-notes/notes/kaggle-fin.html)
- GitHub (7th place): [michaelpoluektov/orvp](https://github.com/michaelpoluektov/orvp)

**Quantiacs Competition - Dr. Kodiak (Multiple Wins)**
- Momentum-based futures trading
- ATR-based risk management
- Portfolio: $2.5M real money
- Earnings: $40K+ per quarter
- Platform: Quantiacs.com

### 9.2 Key GitHub Repositories

**Backtesting & Frameworks:**
- [JSteveT/algorithmic-trading-strategies](https://github.com/JSteveT/algorithmic-trading-strategies)
  - Python + Backtrader
  - RSI, Moving Averages
  - Interactive dashboard

- [FranklineMisango/Lumibot_Algorithms](https://github.com/FranklineMisango/Lumibot_Algorithms)
  - High-frequency trading strategies
  - Clean code structure
  - Multiple strategy examples

**Data & Tools:**
- Backtrader: Official documentation
- yfinance: For historical data
- Oanda API: For Forex data
- TradingView: Pine Script reference

### 9.3 Learning Resources

**ICT (Inner Circle Trader) Concepts:**
- Order blocks, Fair Value Gaps
- Liquidity concepts
- Market structure
- Smart Money Concepts (SMC)

**Mean Reversion:**
- Bollinger Bands strategies
- RSI divergence trading
- Statistical arbitrage

**Risk Management:**
- ATR-based position sizing
- Kelly Criterion
- Maximum drawdown management

### 9.4 Tools & Technologies

**Python Ecosystem:**
- pandas: Data manipulation
- numpy: Numerical computing
- backtrader: Backtesting
- scikit-learn: ML/clustering
- matplotlib/plotly: Visualization

**TradingView:**
- Pine Script v5
- Built-in indicators
- Alert system
- Mobile app

**Data Sources:**
- Yahoo Finance (yfinance)
- Oanda API
- MetaTrader 4/5

---

## 10. Notes & Decisions Log

### Key Decisions Made

**December 12, 2024:**
- ✅ Chose Optiver-inspired ensemble approach
- ✅ Decided on two-track system (Python + Pine Script)
- ✅ Selected 8-week timeline (20 hrs/week)
- ✅ Chose standard approach (full 50+ features)
- ✅ Confirmed manual trading execution
- ✅ Prioritized risk management features

**Rationale:**
- Optiver approach proven in competition
- Two-track gives best of both worlds
- 8 weeks allows proper development
- Full features = professional quality
- Manual execution = prop firm requirement

### Design Principles

1. **Quality over Speed**: Take time to do it right
2. **Test Everything**: Rigorous validation
3. **Document Well**: Future-proof the code
4. **Keep It Simple**: Avoid over-complication
5. **Stay Flexible**: Adapt as we learn

### Open Questions

- [ ] Which specific Forex pairs to focus on?
- [ ] Oanda API key needed? (can add later)
- [ ] Streamlit dashboard priority? (optional)
- [ ] Trade journaling format preference?
- [ ] Preferred notification method?

---

## 11. Appendix

### A. File Naming Conventions

**Python Files:**
- snake_case for files: `ict_strategy.py`
- PascalCase for classes: `class ICTStrategy`
- lowercase for functions: `def calculate_order_blocks()`

**Pine Script Files:**
- lowercase with hyphens: `ict-signals.pine`
- Descriptive names: `ensemble-dashboard.pine`

**Data Files:**
- Format: `{PAIR}_{TIMEFRAME}.csv`
- Example: `EURUSD_H1.csv`, `GBPUSD_M15.csv`

### B. Configuration Management

**config.yaml structure:**
```yaml
data:
  pairs: [EURUSD, GBPUSD, XAUUSD]
  timeframes: [M15, H1, H4]
  period: 2y

strategy:
  ict:
    min_confidence: 70
    order_block_threshold: 3
  mean_reversion:
    rsi_threshold: 30
    bollinger_std: 2.5

risk:
  atr_stop_multiplier: 2.0
  atr_tp_multiplier: 3.0
  max_risk_percent: 0.02
```

### C. Performance Tracking Template

**Metrics to Track Daily:**
- Total trades
- Win/loss count
- Average win/loss size
- Largest win/loss
- Current drawdown
- Signal confidence levels

**Weekly Review:**
- Weekly P&L
- Win rate
- Average RRR achieved
- Strategy breakdown (ICT vs MR)
- Market conditions

**Monthly Analysis:**
- Monthly returns
- Sharpe ratio
- Max drawdown
- Strategy adjustments needed
- Parameter updates

---

## 12. Change Log

| Date | Version | Changes |
|------|---------|---------|
| 2024-12-12 | 1.0 | Initial project plan created |
| 2024-12-12 | 1.0 | Environment setup completed |

---

## 13. Contact & Support

**Developer:** JC  
**Project Location:** `/Users/jc/Desktop/algo trading/pinescript/`  
**Documentation:** This file (PROJECT_PLAN.md)  
**Repository:** (To be set up if desired)  

---

**End of Project Plan**

*Last Updated: December 12, 2024*  
*Next Review: End of Week 1 (December 22, 2024)*

---

## 🎯 Quick Reference

**Current Status:** Week 1, Phase 2 - Foundation  
**Hours Completed:** 1 / 160  
**Progress:** 0.6%  
**Next Milestone:** Complete data fetching system (10 hours)  
**Target Go-Live:** February 10-16, 2025  

**Remember:**
- Python = Research & development (monthly updates)
- Pine Script = Live trading signals (daily use)
- You = Final decision maker (manual execution)

**Let's build something great! 🚀**

