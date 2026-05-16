---
description: Smart stock screening workflow - Filter quality targets based on multi-factor model
---

# Smart Stock Screening Workflow

Based on multi-factor model, filter quality targets from the market that meet technical and fundamental conditions, providing comprehensive scoring and buy recommendations.

## Execution Steps

### Step 1: Understand Screening Criteria

Extract from user input:
- **Market scope**: Country/region (determine market_code), asset type
- **Technical conditions**: Trend direction, RSI range, MACD status, volume
- **Fundamental conditions**: PE, PB, ROE, market cap, dividend yield, etc.
- **Sorting preference**: Change percentage, market cap, volume, etc.

### Step 2: Select Market and Screener Preset

tvremix uses market names directly (e.g., 'america', 'china') and built-in screener presets — no separate metadata call needed.

```
# tvremix uses market names directly — no metadata call required
# Available markets: america, china, hongkong, japan, etc.
# Use run_screener with filter_preset or custom filters
```

### Step 3: Get Candidate Pool

Use run_screener or analyze_sector_tool based on screening direction:

```
# Technical screening - sort by performance
run_screener(
  market='china', sort_by='change', sort_order='desc', limit=100
)

# Fundamental data - use filter_preset or custom filters
run_screener(
  market='china', filter_preset='value', sort_by='market_cap', limit=100
)

# Sector-based screening
analyze_sector_tool(
  sector_name='Technology', market='china', metric='market_cap', limit=100
)
```

**tvremix-specific tools for smarter screening**:
- `rank_symbol_setups(symbols, focus='momentum')` — rank a symbol list by tradable setups
- `filter_by_indicator(symbols, indicator='rsi', comparator='within_pct')` — filter by indicator levels

### Step 4: Technical Screening

For Top 20-30 in candidate pool, call individually:

```
get_technicals(symbol, interval='1D')
```

Screening criteria (see `references/technical-analysis.md` scoring model):
- TA multi-timeframe signal is Buy
- RSI in healthy range 30-70
- MACD golden cross or DIF > 0
- ADX > 25 (trend exists)

### Step 5: K-line Data Verification

For Top 10 that pass technical screening, get K-line confirmation:

```
get_ohlcv(symbol, interval='1D', count=60)
```

Verify:
- Moving average arrangement (bullish/bearish)
- Volume coordination (volume increase on rise)
- Distance from support level

### Step 6: Comprehensive Scoring and Ranking

Calculate total score (100-point system) according to `references/technical-analysis.md` scoring model:
- Trend strength 30 points
- Momentum indicators 25 points
- Pattern recognition 20 points
- Support resistance 15 points
- Market sentiment 10 points

### Step 7: Generate Detailed Report

```markdown
# Smart Stock Screening Results - [Market/Sector]

## Screening Criteria
- [List technical and fundamental conditions]

## Qualified Stocks (Total N stocks)

### 1. [Stock Name] (Code) ⭐⭐⭐⭐⭐
**Comprehensive Score**: XX/100
- Technical: RSI=XX, MACD=XX, Trend=XX
- Fundamental: PE=XX, ROE=XX%
- Buy Recommendation: ¥XX-XX
- Stop Loss: ¥XX
- Target Price: ¥XX
```

## Example

**User**: "Help me select strong stocks from China A-shares"

**Execution**:
1. Use market='china' directly (no metadata call needed)
2. `run_screener(market='china', sort_by='change', sort_order='desc', limit=100)` → Top gainers
3. `run_screener(market='china', filter_preset='value', limit=100)` → Valuation data
4. Top 20 individual `get_technicals(symbol, interval='1D')` → Technical screening
5. Top 10 `get_ohlcv(symbol, interval='1D', count=60)` → K-line verification
6. Comprehensive scoring → Output Top 10 report
