# Complete Guide: AI Prompts for Crypto Technical Analysis & Scalping

> **Your Complete Reference for AI-Powered Trading Analysis**

---

## 📖 Table of Contents

1. [Overview & Strategy](#overview--strategy)
2. [Core AI Prompt Templates](#core-ai-prompt-templates)
3. [Data Preparation](#data-preparation)
4. [Scenario-Specific Prompts](#scenario-specific-prompts)
5. [Multi-Timeframe Analysis](#multi-timeframe-analysis)
6. [Advanced Scalping Prompts](#advanced-scalping-prompts)
7. [Validation & Accuracy](#validation--accuracy)
8. [Risk Management Integration](#risk-management-integration)
9. [Quick Reference Templates](#quick-reference-templates)
10. [Trading Journal Integration](#trading-journal-integration)

---

## Overview & Strategy

### Trading Profile
- **Style:** Scalping
- **Timeframes:** 15m, 1h, 4h, 1D
- **Focus:** Crypto markets
- **Goal:** High-probability, quick execution setups

### AI Usage Philosophy
- AI enhances analysis, doesn't replace judgment
- Always verify AI calculations and levels
- Combine multiple AI models for confirmation
- Use structured prompts for consistent results

---

## Core AI Prompt Templates

### 🎯 Master Template for Technical Analysis

```markdown
I'm analyzing [CRYPTO_PAIR] for scalping opportunities. Please provide technical analysis based on this data:

**Current Market Data:**
- Price: $[CURRENT_PRICE]
- Timeframe: [15m/1h/4h/1D]
- Recent High: $[HIGH]
- Recent Low: $[LOW]
- Volume: [VOLUME_DATA]

**Technical Indicators:**
- RSI (14): [VALUE]
- MACD: [MACD_LINE], Signal: [SIGNAL_LINE], Histogram: [HISTOGRAM]
- EMA 20: $[EMA20]
- EMA 50: $[EMA50]
- Bollinger Bands: Upper: $[UPPER], Middle: $[MIDDLE], Lower: $[LOWER]
- Support: $[SUPPORT_LEVEL]
- Resistance: $[RESISTANCE_LEVEL]

**Market Context:**
- Overall trend: [BULLISH/BEARISH/SIDEWAYS]
- Bitcoin dominance: [BTC_DOM]%
- Market sentiment: [FEAR_GREED_INDEX]

Please analyze:
1. Entry opportunities for scalping (15m-1h)
2. Key support/resistance levels
3. Risk/reward ratios
4. Stop loss and take profit levels
5. Market confluence factors

**Risk Parameters:**
- Maximum risk per trade: 0.5%
- Target profit: 1-3%
- Maximum hold time: 30 minutes
```

### 🚀 Quick Analysis Template

```markdown
Quick scalp analysis for [CRYPTO]:

**Current Setup:**
- Price: $[PRICE]
- Timeframe: [TF]
- Key level: $[LEVEL]
- RSI: [VALUE]
- Volume: [NORMAL/HIGH/LOW]

**Question:** Is this a high-probability scalp setup?
**Need:** Entry, SL, 2-3 TP levels, confidence score (1-10)
**Time constraint:** Next 5 minutes
```

---

## Data Preparation

### Essential Data Points Checklist

```markdown
Before submitting AI prompt, gather:

**Price Data:**
- [ ] Current price
- [ ] Recent high/low (last 24h)
- [ ] Key support/resistance levels
- [ ] Previous session high/low

**Technical Indicators:**
- [ ] RSI (14 period)
- [ ] MACD (12,26,9)
- [ ] EMA 20 & EMA 50
- [ ] Bollinger Bands (20,2)
- [ ] Volume vs average

**Market Context:**
- [ ] Bitcoin dominance
- [ ] Fear & Greed Index
- [ ] Trading session (Asian/EU/NY)
- [ ] Recent news/events
```

### Data Formatting Example

```markdown
**From TradingView to AI Prompt:**

Raw TradingView Data:
- RSI(14) = 65.23
- MACD = 12.45, 8.32, 4.13
- Price = $43,250.50

Formatted for AI:
- RSI (14): 65.23 (approaching overbought territory)
- MACD: Line 12.45, Signal 8.32, Histogram 4.13 (bullish momentum confirmed)
- Current Price: $43,250.50 (testing key resistance zone)
```

---

## Scenario-Specific Prompts

### 💥 Breakout Analysis

```markdown
Analyze this potential breakout setup for [CRYPTO]:

**Price Action:**
- Current: $[PRICE]
- Resistance being tested: $[RESISTANCE]
- Volume on approach: [VOLUME] vs avg [AVG_VOLUME]
- Previous breakouts at this level: [SUCCESS_RATE]%

**Confluence Factors:**
- RSI: [VALUE] (momentum confirmation?)
- Volume profile: [THIN/THICK] above resistance
- Time of day: [TIME] (liquidity consideration)
- Higher timeframe bias: [BULLISH/BEARISH]

**Questions:**
1. Is this a high-probability breakout for scalping?
2. What are the entry criteria?
3. Provide 3 take profit levels with R:R ratios
4. Where should stop loss be placed?
5. What invalidates this setup?

**Risk tolerance:** Maximum 0.5% account risk
```

### 📉 Mean Reversion Setup

```markdown
Evaluate this mean reversion opportunity:

**Deviation Data:**
- Current price: $[PRICE]
- Distance from EMA20: [PERCENTAGE]%
- Bollinger Band position: [LOWER/MIDDLE/UPPER]
- RSI: [VALUE] (oversold/overbought level)

**Market Structure:**
- Higher timeframe trend: [DIRECTION]
- Key support below: $[SUPPORT]
- Recent rejection candles: [COUNT]
- Volume on decline: [DECREASING/INCREASING]

**Assessment needed:**
1. Is this suitable for mean reversion scalping?
2. What's the probability of bounce?
3. Entry trigger and timing
4. Target back to which level?
5. Risk level: [LOW/MEDIUM/HIGH]

**Context:** Looking for quick 1-2% bounce trade
```

### ⚡ Momentum Continuation

```markdown
Momentum analysis for [CRYPTO] scalping:

**Current Momentum:**
- Price movement: [PERCENTAGE]% in [TIME_PERIOD]
- Volume: [VOLUME] ([X]x average)
- RSI: [VALUE] (momentum strength)
- MACD: [STATUS] (accelerating/decelerating)

**Structure:**
- Previous impulse: [DESCRIPTION]
- Current pullback: [DEPTH]%
- Next resistance: $[LEVEL]

**Strategy Assessment:**
1. Is momentum likely to continue?
2. Best entry for continuation trade
3. Quick scalp targets (1-3%)
4. Momentum failure signals

**Execution timeframe:** 15m entries, 5-30 min holds
```

---

## Multi-Timeframe Analysis

### 🕐 Complete MTF Analysis Template

```markdown
Multi-timeframe analysis for [CRYPTO] scalping:

**Daily (1D) - Overall Context:**
- Trend direction: [BULLISH/BEARISH/SIDEWAYS]
- Key level proximity: $[LEVEL] ([DISTANCE] away)
- RSI: [VALUE] (trend strength)
- Volume trend: [INCREASING/DECREASING/STABLE]

**4-Hour - Intermediate Structure:**
- Current structure: [UPTREND/DOWNTREND/RANGE]
- EMA alignment: [BULLISH/BEARISH/MIXED]
- Support/Resistance: $[SUPPORT] / $[RESISTANCE]
- Momentum: [STRONG/WEAK/NEUTRAL]

**1-Hour - Setup Timeframe:**
- Pattern developing: [PATTERN_TYPE]
- Entry setup quality: [HIGH/MEDIUM/LOW]
- Next key level: $[LEVEL]
- Volume participation: [GOOD/POOR]

**15-Minute - Execution Timeframe:**
- Current microstructure: [DESCRIPTION]
- Entry trigger: [SPECIFIC_CONDITION]
- Immediate S/R: $[SUPPORT] / $[RESISTANCE]
- Scalp opportunity: [YES/NO/WAIT]

**Scalping Strategy:**
Provide strategy with timeframe-based confirmations:
1. Higher timeframe bias confirmation
2. Intermediate structure support
3. Entry timeframe trigger
4. Risk management across timeframes
```

---

## Advanced Scalping Prompts

### ⚡ Ultra-Quick Momentum Scalp

```markdown
URGENT: Quick momentum analysis for immediate scalping

**Flash Setup:** 
- Crypto: [SYMBOL]
- Just broke: $[LEVEL] with [VOLUME_DESCRIPTION]
- Timeframe: 15m
- Current momentum: RSI [VALUE], volume [STATUS]

**Immediate Questions:**
1. Momentum continuation or false breakout?
2. Quick entry point (next 2-3 minutes)
3. Two rapid TP levels (1% and 2%)
4. Tight stop loss placement
5. Maximum hold time recommendation

**Execution Constraint:** Need decision in next 5 minutes
**Risk:** 0.5% maximum account risk
```

### 🎯 Range Trading Scalp

```markdown
Range scalping analysis for [CRYPTO]:

**Range Definition:**
- Upper boundary: $[HIGH] (tested [X] times)
- Lower boundary: $[LOW] (tested [Y] times)
- Current position: $[PRICE] ([PERCENTAGE]% of range)
- Range duration: [TIME_PERIOD]

**Range Characteristics:**
- Average bounce distance: [DISTANCE] ([PERCENTAGE]%)
- Success rate of bounces: [SUCCESS_RATE]%
- Typical time to opposite boundary: [TIME]
- Volume pattern: [DESCRIPTION]

**Current Analysis:**
- Distance to nearest boundary: $[DISTANCE]
- Quality of current level: [HIGH/MEDIUM/LOW]
- Entry criteria for range play
- Position sizing for range trade

**Strategy:** Buy support, sell resistance
**Risk:** Quick exit if range breaks
```

### 📰 News Event Scalping

```markdown
Pre/Post news scalping setup analysis:

**Event Details:**
- Event: [NEWS_EVENT]
- Time until/since release: [DURATION]
- Expected impact: [HIGH/MEDIUM/LOW]
- Market anticipation: [PRICED_IN/SURPRISE_POTENTIAL]

**Current Technical State:**
- Price: $[PRICE]
- Key levels: $[SUPPORT] / $[RESISTANCE]
- Current volatility: [CURRENT] vs normal [NORMAL]
- Volume: [STATUS]

**Strategy Options:**
1. **Pre-news positioning:**
   - Position bias and reasoning
   - Risk management for volatility spike
   
2. **Post-news momentum:**
   - Reaction scalping strategy
   - Quick profit targets
   
3. **Risk Management:**
   - Position sizing adjustment
   - Stop loss strategy for volatility
   - Exit criteria if news against position

**Execution Plan:** [PRE/POST] news strategy with tight risk control
```

---

## Validation & Accuracy

### 🔍 Analysis Verification Template

```markdown
Please review this analysis for accuracy and completeness:

[PASTE PREVIOUS AI RESPONSE HERE]

**Verification Checklist:**
1. Are technical indicator interpretations correct?
2. Do support/resistance levels align with recent price action?
3. Is the risk/reward calculation mathematically accurate?
4. Are there any contradictions in the analysis?
5. Does the timeframe analysis make logical sense?

**Accuracy Assessment:**
- Technical accuracy (1-10): 
- Risk assessment realism (1-10):
- Entry criteria clarity (1-10):
- Overall confidence (1-10):

**Corrections needed:**
[List any corrections or clarifications]

**Additional considerations:**
[Any missed factors or alternative scenarios]
```

### 📊 Cross-Reference Method

```markdown
**Step 1:** Get analysis from multiple AI models
**Step 2:** Compare conclusions using this template:

**AI Model Comparison for [CRYPTO] Analysis:**

| Factor | ChatGPT | Claude | Consensus |
|--------|---------|---------|-----------|
| Entry Level | $[X] | $[Y] | $[Z] |
| Stop Loss | $[X] | $[Y] | $[Z] |
| Take Profit 1 | $[X] | $[Y] | $[Z] |
| Take Profit 2 | $[X] | $[Y] | $[Z] |
| Confidence | [X]/10 | [Y]/10 | [Z]/10 |
| Risk Level | [X] | [Y] | [Z] |

**Consensus Decision:**
- Entry: $[FINAL_ENTRY]
- Stop: $[FINAL_STOP]
- Targets: $[TP1], $[TP2]
- Overall confidence: [FINAL_CONFIDENCE]/10

**Proceed with trade:** [YES/NO/WAIT]
```

---

## Risk Management Integration

### ⚠️ Pre-Trade Risk Assessment

```markdown
Before executing this trade, verify risk parameters:

**Trade Setup:** [BRIEF_DESCRIPTION]
**Account size:** $[AMOUNT]
**Risk per trade:** 0.5% = $[AMOUNT]

**Position Sizing Calculation:**
- Entry: $[ENTRY_PRICE]
- Stop Loss: $[STOP_LOSS]
- Risk per unit: $[RISK_PER_UNIT]
- Position size: [UNITS] = $[POSITION_VALUE]

**Risk Verification Questions:**
1. Is position size correct for 0.5% account risk?
2. Is stop loss logical and not too tight for volatility?
3. Am I overtrading or is this genuinely high probability?
4. What could invalidate this setup quickly?
5. How does this fit my daily/weekly risk budget?

**Risk Budget Status:**
- Trades today: [COUNT]
- Risk used today: [PERCENTAGE]%
- Remaining risk budget: [PERCENTAGE]%

**Proceed:** [YES/NO] - Reason: [EXPLANATION]
```

### 🛡️ Position Management Template

```markdown
Active position management for [CRYPTO] scalp:

**Position Details:**
- Entry: $[ENTRY] at [TIME]
- Current: $[CURRENT_PRICE]
- P&L: [PERCENTAGE]% ($[AMOUNT])
- Time in trade: [DURATION]

**Current Status:**
- Stop loss: $[CURRENT_STOP]
- Next target: $[TARGET]
- Market conditions: [STATUS]

**Management Decisions:**
1. Should I move stop to breakeven?
2. Partial profit taking opportunity?
3. Target extension or take profits?
4. Time-based exit consideration?
5. Market structure changes affecting trade?

**Updated Plan:**
- Action: [HOLD/SCALE_OUT/EXIT/ADJUST_STOP]
- New stop: $[NEW_STOP]
- Remaining target: $[TARGET]
- Max time remaining: [TIME]
```

---

## Quick Reference Templates

### ⚡ Lightning Analysis (2-Minute Response)

```markdown
QUICK CHECK: [CRYPTO] [TIMEFRAME]

Current: $[PRICE] | RSI: [VALUE] | Volume: [STATUS]
Setup: [ONE_LINE_DESCRIPTION]

**Decision needed:** Trade or wait?
**Output required:** Entry, SL, TP in 30 seconds
**Risk:** 0.5% max
```

### 📈 Rapid Market Scan

```markdown
Market scan for scalping opportunities:

**Top movers requiring analysis:**
1. [CRYPTO1]: [PRICE] ([CHANGE]%)
2. [CRYPTO2]: [PRICE] ([CHANGE]%)
3. [CRYPTO3]: [PRICE] ([CHANGE]%)

**For each:** Quick probability assessment (1-10) for scalping
**Filter:** Only setups >7/10 probability
**Timeframe:** 15m entries
**Session:** [CURRENT_SESSION]
```

### 🎯 Setup Quality Checker

```markdown
Rate this scalping setup quality:

**Setup Type:** [BREAKOUT/REVERSAL/MOMENTUM/RANGE]
**Confluence factors:** [COUNT] (list them)
**Risk/Reward:** [RATIO]
**Timeframe alignment:** [YES/NO]
**Volume confirmation:** [YES/NO]

**Quality Score:** [X]/10
**Trade:** [YES/NO]
**Reason:** [BRIEF_EXPLANATION]
```

---

## Trading Journal Integration

### 📝 Pre-Trade Journal Entry

```markdown
**Trade Setup Documentation:**

**Date:** [DATE] **Time:** [TIME]
**Symbol:** [CRYPTO] **Timeframe:** [TF]

**Analysis Summary:**
- Setup type: [TYPE]
- Entry reason: [REASON]
- Confluence factors: [LIST]
- AI confidence: [X]/10

**Risk Parameters:**
- Entry: $[ENTRY]
- Stop Loss: $[STOP]
- Take Profit 1: $[TP1]
- Take Profit 2: $[TP2]
- Risk amount: $[RISK]
- R:R ratio: [RATIO]

**Market Context:**
- Session: [SESSION]
- Overall bias: [BIAS]
- Key news: [NEWS]

**Expected outcome:** [DESCRIPTION]
```

### 📊 Post-Trade Review

```markdown
**Trade Review and Analysis:**

**Trade Summary:**
- Entry: $[ENTRY] at [TIME]
- Exit: $[EXIT] at [TIME]
- Result: [WIN/LOSS] ([PERCENTAGE]%)
- Hold time: [DURATION]

**Execution Analysis:**
- Entry timing: [EXCELLENT/GOOD/POOR]
- Exit timing: [EXCELLENT/GOOD/POOR]
- Risk management: [EXCELLENT/GOOD/POOR]

**What worked:**
- [FACTOR 1]
- [FACTOR 2]

**What didn't work:**
- [FACTOR 1]
- [FACTOR 2]

**Lessons learned:**
- [LESSON 1]
- [LESSON 2]

**Similar setups:** Compare to [PREVIOUS_TRADE_DATE]
**Pattern success rate:** [PERCENTAGE]%
**Improvement areas:** [SPECIFIC_AREAS]
```

### 📈 Daily Performance Review

```markdown
**Daily Trading Performance Review:**

**Statistics:**
- Total trades: [COUNT]
- Wins: [COUNT] ([PERCENTAGE]%)
- Losses: [COUNT] ([PERCENTAGE]%)
- Average R:R: [RATIO]
- Net P&L: [AMOUNT] ([PERCENTAGE]%)

**Best trade:** [DESCRIPTION] (+[PERCENTAGE]%)
**Worst trade:** [DESCRIPTION] (-[PERCENTAGE]%)

**Pattern Performance:**
- Breakouts: [WIN_RATE]%
- Reversals: [WIN_RATE]%
- Momentum: [WIN_RATE]%

**Session Performance:**
- Asian: [RESULT]
- European: [RESULT]
- NY: [RESULT]

**Tomorrow's focus:**
- [IMPROVEMENT_AREA_1]
- [IMPROVEMENT_AREA_2]
- [SETUP_TYPE_TO_FOCUS]

**Risk management grade:** [A/B/C/D/F]
**Discipline grade:** [A/B/C/D/F]
```

---

## Emergency Templates

### 🚨 Position In Trouble

```markdown
URGENT: Position management help needed

**Current situation:**
- Position: [LONG/SHORT] [CRYPTO] at $[ENTRY]
- Current price: $[CURRENT]
- Unrealized P&L: -[PERCENTAGE]%
- Time in trade: [DURATION]

**Problem:** [DESCRIBE_ISSUE]

**Options analysis needed:**
1. Hold and hope for recovery?
2. Cut losses now?
3. Average down (if appropriate)?
4. Adjust stop loss?

**Market context:** [CHANGED/UNCHANGED]
**Original thesis:** [VALID/INVALID]

**Decision needed:** Next 2 minutes
```

### 🔥 Rapid Market Change

```markdown
MARKET ALERT: Sudden price movement

**Event:** [CRYPTO] moved [PERCENTAGE]% in [TIME_PERIOD]
**Trigger:** [NEWS/TECHNICAL/UNKNOWN]
**Current price:** $[PRICE]

**Immediate assessment needed:**
1. Is this a scalping opportunity?
2. Entry level for momentum play?
3. Quick targets and stops?
4. Risk of reversal?

**Action required:** [ENTER/WAIT/PREPARE]
**Timeframe:** 15m execution
```

---

## Advanced Automation Scripts

### 🤖 Automated Prompt Generation

```python
# Example structure for automated prompt creation
def generate_crypto_prompt(symbol, timeframe, analysis_type="scalping"):
    # Fetch real-time data
    data = get_market_data(symbol, timeframe)
    indicators = calculate_indicators(data)
    
    prompt = f"""
    {analysis_type.title()} analysis for {symbol} on {timeframe}:
    
    **Current Data:**
    - Price: ${data['close']:.2f}
    - RSI: {indicators['rsi']:.1f}
    - MACD: {indicators['macd']['macd']:.2f}
    - Volume: {data['volume']:,.0f} ({indicators['volume_ratio']:.1f}x avg)
    
    **Key Levels:**
    - Support: ${indicators['support']:.2f}
    - Resistance: ${indicators['resistance']:.2f}
    - EMA20: ${indicators['ema20']:.2f}
    
    **Context:**
    - Session: {get_trading_session()}
    - BTC Dominance: {get_btc_dominance():.1f}%
    
    Provide {analysis_type} strategy for next 15-30 minutes.
    Risk: 0.5% max, Target: 1-3%, Hold: <30 min
    """
    
    return prompt
```

---

## Final Checklist

### ✅ Before Every Trading Session

```markdown
**Pre-Session Checklist:**

**Technical Setup:**
- [ ] Charts loaded and indicators set
- [ ] Key levels marked
- [ ] Economic calendar checked
- [ ] AI prompts ready and tested

**Risk Management:**
- [ ] Daily risk budget calculated
- [ ] Position sizing calculator ready
- [ ] Stop loss rules confirmed
- [ ] Maximum trades per day set

**Mental Preparation:**
- [ ] Trading plan reviewed
- [ ] Recent performance analyzed
- [ ] Mindset check completed
- [ ] Distractions eliminated

**AI Strategy:**
- [ ] Prompt templates ready
- [ ] Multiple AI models accessible
- [ ] Validation process confirmed
- [ ] Journal template prepared
```

### 🎯 Success Metrics

```markdown
**Weekly Success Evaluation:**

**Performance Metrics:**
- Win rate target: >60%
- Average R:R target: >1.5
- Maximum daily loss: <2%
- Consistency: Positive 4/5 days

**AI Usage Effectiveness:**
- Prompt accuracy: >70%
- Setup quality improvement: Measurable
- Risk management: Enhanced
- Decision speed: Faster

**Continuous Improvement:**
- [ ] Refine prompt templates
- [ ] Update validation process  
- [ ] Enhance risk parameters
- [ ] Optimize timeframe analysis
```

---

**⚠️ Important Disclaimers:**

*This guide is for educational purposes only. Cryptocurrency trading involves significant risk of loss. Past performance does not guarantee future results. Always:*

- *Use proper position sizing and risk management*
- *Never risk more than you can afford to lose*
- *Verify all AI analysis with your own research*
- *This is not financial advice*
- *Consult with financial professionals as needed*

---

**📌 Quick Access Links:**
- [Master Template](#core-ai-prompt-templates)
- [Quick Analysis](#quick-reference-templates)
- [Risk Management](#risk-management-integration)
- [Journal Templates](#trading-journal-integration)

---

*Last Updated: [DATE] | Version: 1.0*
*Keep this guide updated with your trading experience and market changes*