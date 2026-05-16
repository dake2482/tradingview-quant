---
description: Multi-Timeframe Analysis Workflow - Cross-period trend confirmation and entry timing selection
---

# Multi-Timeframe Analysis Workflow

Use candlestick data and technical indicators across multiple timeframes to confirm trend direction consistency and select optimal entry timing.

## Core Concept

**Higher timeframe defines direction, lower timeframe finds entry**: Monthly/weekly confirms primary trend, daily confirms medium-term trend, hourly selects entry point.

## Execution Steps

### Step 1: Get Multi-Period Chart Data

Call in parallel to get 4 timeframes:

```
get_ohlcv(symbol, interval='1M', count=24)    # Monthly - 2 years
get_ohlcv(symbol, interval='1W', count=52)    # Weekly - 1 year
get_ohlcv(symbol, interval='1D', count=120)   # Daily - 6 months
get_ohlcv(symbol, interval='1h', count=120)   # Hourly - 5 days
```

Optional: tvremix has no Heikin Ashi mode; use standard OHLCV data and compute Heikin Ashi values client-side if needed.

**tvremix built-in multi-TF shortcut**: Use `analyze_multi_timeframe(symbol, timeframes=['1D', '1W', '1h', '1M'])` to get aggregated multi-timeframe trend alignment in one call, including per-TF bias and an overall alignment score.

### Step 2: Get Technical Analysis Signals

```
get_full_technicals(symbol)
```

The tool returns multi-timeframe signals (15m/1h/4h/1D/1W by default) directly providing buy/sell/neutral signal aggregation for each timeframe.

### Step 3: Trend Assessment for Each Period

Assess trend direction for each timeframe:

**Monthly (Strategic Direction)**:
- Price above SMA20 → Long-term uptrend
- Price below SMA20 → Long-term downtrend
- MACD direction confirmation

**Weekly (Tactical Direction)**:
- Moving average alignment (SMA5 > SMA10 > SMA20 = bullish)
- RSI position (40-70 healthy uptrend range)
- MACD golden cross/death cross status

**Daily (Operating Period)**:
- Short-term vs medium-term moving average relationship
- Volume cooperation (volume surge on rise/volume contraction on pullback)
- Support/resistance levels

**Hourly (Entry Timing)**:
- Pullback near daily support level
- RSI bouncing from oversold zone
- Bullish candlestick pattern appears

### Step 4: Trend Consistency Assessment

| Monthly | Weekly | Daily | Signal Strength | Trading Recommendation |
|---------|--------|-------|----------------|------------------------|
| ↑ | ↑ | ↑ | Strong Bull | Aggressive long, trend following |
| ↑ | ↑ | ↓ | Medium Bull | Wait for daily pullback stabilization before buying |
| ↑ | ↓ | ↓ | Weak Bull | Wait and see, wait for weekly stabilization |
| ↓ | ↓ | ↓ | Strong Bear | Avoid or short |
| ↓ | ↓ | ↑ | Weak Bear | Likely a bounce, not suitable for chasing |
| ↓ | ↑ | ↑ | Medium Bear | Possible early reversal, light position test |

### Step 5: Generate Analysis Report

```markdown
# [Symbol] Multi-Timeframe Analysis

## Trend Status by Period
| Period | Trend | Key Indicators | TA Signal |
|--------|-------|----------------|-----------|
| Monthly | ↑/↓/→ | SMA20, MACD | Buy/Sell/Neutral |
| Weekly | ↑/↓/→ | MA alignment, RSI | Buy/Sell/Neutral |
| Daily | ↑/↓/→ | Volume, MA | Buy/Sell/Neutral |
| Hourly | ↑/↓/→ | Short-term momentum | Buy/Sell/Neutral |

## Trend Consistency: [Strong Bull/Medium Bull/Weak Bull/Neutral/Weak Bear/Strong Bear]

## Key Price Levels
- Monthly support: ¥XX
- Weekly support: ¥XX
- Daily support: ¥XX
- Daily resistance: ¥XX

## Trading Recommendations
- Direction: ...
- Entry conditions: ...
- Stop loss: ...
- Target: ...
```

## Example

**User**: "Multi-timeframe analysis of BTCUSDT"

**Execution**:
1. `get_ohlcv` x 4 timeframes (1M/1W/1D/1h)
2. `get_full_technicals(symbol)` → Multi-period signals
3. Assess trend consistency across periods
4. Identify key support/resistance levels
5. Output trend consistency report and entry recommendations

**tvremix shortcut**: `analyze_multi_timeframe(symbol='BINANCE:BTCUSDT', timeframes=['1M', '1W', '1D', '1h'])` provides the full multi-TF alignment in one call.
