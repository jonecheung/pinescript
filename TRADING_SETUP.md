# 🎯 Quick Reference - Trading Setup

**Your Specific Configuration**  
*Last Updated: December 12, 2024*

---

## 📊 **Instruments (Micro Futures)**

### **MES - Micro E-mini S&P 500** (40% of trades)
```
TradingView: MES1!
YFinance: ES=F
Contract: $5 per point
Tick: 0.25 points = $1.25
Typical ATR: 30 points
Typical Stop: 60 points (2×ATR) = $300 per contract

Position Sizing ($50K account):
├─ 1% risk ($500): 1 contract
├─ 1.5% risk ($750): 2 contracts
└─ 2% risk ($1000): 3 contracts

Why Primary: Most liquid, stable trends, perfect ICT setups
```

### **MNQ - Micro NASDAQ-100** (30% of trades)
```
TradingView: MNQ1!
YFinance: NQ=F
Contract: $2 per point
Tick: 0.25 points = $0.50
Typical ATR: 50 points
Typical Stop: 100 points (2×ATR) = $200 per contract

Position Sizing ($50K account):
├─ 1% risk ($500): 2 contracts
├─ 1.5% risk ($750): 3 contracts
└─ 2% risk ($1000): 5 contracts

Why Primary: High volatility, tech-driven, strong trends
```

### **MGC - Micro Gold** (30% of trades)
```
TradingView: MGC1!
YFinance: GC=F
Contract: $1 per point (10 troy oz)
Tick: $0.10 = $0.10
Typical ATR: $20
Typical Stop: $40 (2×ATR) = $40 per contract

Position Sizing ($50K account):
├─ 1% risk ($500): 12 contracts
├─ 1.5% risk ($750): 18 contracts
└─ 2% risk ($1000): 25 contracts

Why Secondary: Diversification, safe-haven, different market driver
```

---

## ⏰ **Trading Schedule (Kill Zones ONLY)**

### **London Kill Zone**
```
Time: 2:00 AM - 5:00 AM EST (7:00-10:00 GMT)
Risk: Conservative (1% per trade = $500)
Focus: All instruments
Setup: Asian session liquidity sweeps + European open
```

### **New York Kill Zone** ⭐ PRIMARY
```
Time: 7:00 AM - 10:00 AM EST (12:00-15:00 GMT)
Risk: Moderate (1-1.5% per trade = $500-750)
Focus: MES, MNQ (US indices)
Setup: NY open + overnight liquidity sweeps
```

### **⚠️ NO TRADING:**
- Outside kill zones (low probability)
- Asian session (unless major news)
- After 10 AM EST (chop/consolidation)
- Fridays after 2 PM EST (weekend prep)

---

## 💰 **Prop Firm Rules (FundedHive)**

### **HARD LIMITS (Never Exceed!):**
```
Per Trade Loss: 3% max = $1,500
Daily Loss: 5% max = $2,500
Overall Drawdown: 10% max = $5,000
Weekend Holding: ❌ NOT ALLOWED (when funded)
News Trading: ✅ ALLOWED
```

### **Our Conservative Approach:**
```
Typical Risk: 1% = $500 per trade
Moderate Risk: 1.5% = $750 per trade
Maximum Risk: 2% = $1,000 per trade
Daily Stop: 4% = $2,000 (buffer below 5%)
Max Trades/Day: 2-3 trades
```

### **Challenge Phases:**
```
Phase 1:
├─ Profit Target: 8% = $4,000
├─ Profitable Days: 3 days required
└─ Time: Unlimited

Phase 2:
├─ Profit Target: 6% = $3,000
├─ Profitable Days: 3 days required
└─ Time: Unlimited

Funded:
├─ Profit Split: 80% to you
├─ No weekend holding
└─ Scale up after consistent profit
```

---

## 📋 **Pre-Trade Checklist**

### **Before Every Trade:**
```
[ ] Is it during a kill zone? (London or NY)
[ ] ICT confidence score > 70?
[ ] Mean reversion score > 70?
[ ] Combined ensemble score > 75?
[ ] Position size calculated correctly?
[ ] Risk < $1,500 (3% limit)?
[ ] Daily loss < $2,000 (our 4% stop)?
[ ] ATR-based stop set?
[ ] Take profit target set (3×ATR)?
[ ] No other conflicting positions?
```

### **Risk Calculation Formula:**
```
1. Get current ATR for instrument
2. Stop Distance = ATR × 2.0
3. Risk Amount = $50,000 × Risk% (1-2%)
4. Contracts = Risk Amount / (Stop Distance × Contract Value)
5. Round DOWN to nearest whole number
6. Verify total risk < $1,500
```

---

## 🎯 **Trade Example**

### **MES Long Setup (NY Kill Zone)**
```
Time: 8:30 AM EST (NY open)
Setup: Order Block + FVG + Liquidity Sweep

Entry: 4500
ATR: 30 points
Stop: 4500 - 60 = 4440 (2×ATR)
Target 1: 4500 + 90 = 4590 (3×ATR)
Target 2: 4500 + 180 = 4680 (6×ATR)

Risk: 1.5% = $750
Contracts: $750 / ($300) = 2.5 → 2 contracts
Actual Risk: 2 × 60 × $5 = $600 ✅
Reward: 2 × 90 × $5 = $900 (1.5:1) ✅

Position Management:
├─ Exit 50% at Target 1 (+$900)
├─ Move stop to breakeven
└─ Trail remaining 50% with 1×ATR
```

---

## 📊 **Daily Tracking**

### **What to Log:**
```
Date & Time:
Session: London / NY
Instrument: MES / MNQ / MGC
Setup Type: ICT / Mean Reversion / Ensemble
Entry Price:
Stop Loss:
Take Profit:
Contracts:
Risk Amount:
Outcome: Win / Loss / Breakeven
P&L:
Notes:
```

### **Daily Limits Check:**
```
Starting Balance: $50,000
Current Balance: $______
Daily P&L: $______
Daily Loss Limit: -$2,000 (our stop)
Remaining Risk: $______ (stop if < $500)

Trades Today: ___ / 3 max
Current Drawdown: ___% / 10% max
```

---

## 🚫 **Stop Trading If:**

```
❌ Lost 4% ($2,000) in one day
❌ Made 3 trades already today
❌ Outside kill zones
❌ Tired/emotional
❌ Multiple losses in a row (2+)
❌ Not following checklist
❌ ATR unusually high (news event)
❌ Friday after 2 PM EST
```

---

## ✅ **Weekly Review**

### **Every Sunday:**
```
1. Total trades this week: ___
2. Win rate: ___% (target: 48-55%)
3. Average RRR achieved: ___ (target: > 1.5)
4. Largest win: $___ / Largest loss: $___
5. Best session: London / NY
6. Best instrument: MES / MNQ / MGC
7. Strategy breakdown: ICT ___% / MR ___%
8. Total P&L: $___ (target: +2% = $1,000/week)
9. Current drawdown: ___% (limit: 10%)
10. What worked well:
11. What needs improvement:
12. Parameter adjustments needed:
```

---

## 📞 **Emergency Contacts**

```
FundedHive Support: [Add contact info]
Prop Firm Dashboard: [Add URL]
cTrader Support: [Add contact info]
TradingView Status: status.tradingview.com
```

---

## 💡 **Quick Tips**

### **London Session:**
- Look for Asian low/high liquidity sweeps
- Conservative 1% risk
- Best for Gold (safe-haven moves)

### **NY Session:**
- Wait for 7-8 AM spike (open volatility)
- Best for MES/MNQ (US indices)
- Highest volume = best ICT setups

### **Risk Management:**
- Never revenge trade after loss
- Take profits at targets (don't get greedy)
- Scale in only if initial position profitable
- Weekend: Close ALL positions by Friday 4 PM

### **Psychology:**
- Trust the system (70%+ confidence)
- Accept losses (part of the game)
- Journal everything (learn and improve)
- Celebrate small wins
- Take breaks after 2 losses

---

**Remember:** The goal is consistency, not home runs!

*Stay disciplined. Follow the plan. Trust the process.* 🎯

