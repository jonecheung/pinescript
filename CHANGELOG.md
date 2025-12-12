# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [Unreleased]

### To Be Added (Week 1)
- Project folder structure
- Data fetchers (yfinance + Oanda)
- Feature engineering framework
- Backtrader data loader

### To Be Added (Week 2-8)
- ICT strategy implementation
- Mean reversion strategy
- Ensemble logic
- Pine Script indicators
- Complete documentation

---

## [0.1.1] - 2024-12-12

### Changed - Updated to Futures Trading
- **Changed instruments** from Forex to Futures (MES, MNQ, MGC)
- **Updated all documentation** to reflect futures trading focus
- **Added prop firm rules** (FundedHive: 3% per trade, 5% daily, 10% overall)
- **Added session filters** (London 2-5 AM, NY 7-10 AM EST only)
- **Updated risk calculations** for micro futures contracts
- **Added instrument specifications** (contract values, tick sizes, typical ATR)
- **Updated config.yaml** with futures-specific settings
- **Updated PROJECT_PLAN.md** with futures details and Dr. Kodiak reference
- **Updated README.md** with trading setup and examples

### Instrument Weighting Decided
- MES (Micro S&P 500): 40% - Primary focus
- MNQ (Micro NASDAQ): 30% - Primary focus  
- MGC (Micro Gold): 30% - Diversification

### Trading Sessions Defined
- London Kill Zone: 2-5 AM EST (conservative 1% risk)
- New York Kill Zone: 7-10 AM EST (primary, 1-1.5% risk)
- No trading outside kill zones

### Account Details Confirmed
- Starting capital: $50,000
- Platform: cTrader via FundedHive
- Profit split: 80% when funded
- Scale up plan: After consistent profitability

---

## [0.1.0] - 2024-12-12

### Added - Initial Setup
- Created project repository
- Set up Python virtual environment (Python 3.12.11)
- Created `requirements.txt` with 19 core packages
- Installed all dependencies (63 packages total including dependencies)
- Created comprehensive `PROJECT_PLAN.md` (13 sections, ~300 lines)
- Created detailed `README.md` with quick start guide
- Created `config.yaml` configuration template
- Created `.gitignore` for Python/IDE files
- Created `CHANGELOG.md` (this file)

### Packages Installed
- **Core Data**: pandas (2.3.3), numpy (2.2.6)
- **Backtesting**: backtrader (1.9.78.123)
- **Data Sources**: yfinance (0.2.66)
- **Technical Indicators**: pandas-ta (0.4.71b0)
- **Machine Learning**: scikit-learn (1.8.0)
- **Visualization**: matplotlib (3.10.8), plotly (6.5.0), seaborn (0.13.2)
- **GUI**: streamlit (1.52.1)
- **Utilities**: pyyaml (6.0.3), python-dotenv (1.2.1), tqdm (4.67.1)

### Documentation Created
1. **PROJECT_PLAN.md** - Master plan with:
   - Executive summary
   - Strategy design (ICT + Mean Reversion)
   - Technical architecture
   - 8-week timeline (160 hours)
   - Success criteria
   - References to competition winners

2. **README.md** - Project overview with:
   - Quick start guide
   - Current status tracking
   - Strategy overview
   - Technology stack
   - Development timeline

3. **config.yaml** - Configuration template with:
   - Data settings (pairs, timeframes)
   - Strategy parameters (ICT, Mean Reversion)
   - Risk management settings
   - Backtesting configuration
   - Feature engineering settings

### Decisions Made
- ✅ Chose Optiver-inspired ensemble approach
- ✅ Two-track system: Python (research) + Pine Script (live)
- ✅ 8-week development timeline (20 hrs/week)
- ✅ Standard approach with full 50+ features
- ✅ Manual execution on cTrader (prop firm)
- ✅ ATR-based risk management

### Progress
- **Time Spent**: 1 hour
- **Completion**: 0.6% (1/160 hours)
- **Current Phase**: Week 1 - Foundation
- **Next Milestone**: Data fetching system (10 hours)

---

## Future Versions (Planned)

### [0.2.0] - Week 1 (Expected: Dec 22, 2024)
- Project folder structure
- Data fetching system (yfinance + Oanda)
- Feature engineering framework (50+ features)
- Backtrader data loader

### [0.3.0] - Week 2-3 (Expected: Jan 5, 2025)
- Complete feature engineering
- ICT strategy implementation
- Initial backtesting results

### [0.4.0] - Week 4-5 (Expected: Jan 19, 2025)
- Mean reversion strategy
- Market regime detection
- Ensemble logic
- Parameter optimization

### [0.5.0] - Week 6-7 (Expected: Feb 2, 2025)
- Pine Script indicators (ICT + Mean Reversion)
- Ensemble dashboard
- ATR-based levels display

### [1.0.0] - Week 8 (Expected: Feb 16, 2025) 🎉
- Final validation
- Complete documentation
- Trading checklist
- **GO LIVE!**

---

## Version History Legend

### Type of Changes
- **Added** - New features
- **Changed** - Changes in existing functionality
- **Deprecated** - Soon-to-be removed features
- **Removed** - Removed features
- **Fixed** - Bug fixes
- **Security** - Security fixes

### Status Indicators
- 🔄 In Progress
- ✅ Completed
- 📋 Planned
- ⚠️ Needs Attention
- 🐛 Bug
- 🎉 Major Milestone

---

*Last Updated: December 12, 2024*

