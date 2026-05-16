---
description: Sector rotation analysis workflow - Identify strong sectors and rotation trends
---

# Sector Rotation Analysis Workflow

Through `run_screener` with performance-based sorting and `analyze_sector_tool` for sector-level analysis, identify current strong sectors, analyze rotation trends, and discover investment opportunities.

## Execution Steps

### Step 1: Confirm Market and Parameters

> **Note**: tvremix uses market names directly (e.g. 'america', 'china', 'japan') and filter/sort parameters instead of metadata endpoints. No separate metadata call is needed.

```
# Market names used directly: 'america', 'china', 'japan', 'korea', etc.
# Use run_screener with sort_by and sort_order to replicate tab-based queries
```

### Step 2: Get Sector Performance Rankings

```
# Gainers - performance data (1W/1M/3M/6M/1Y returns)
run_screener(
  market='china', sort_by='change',
  sort_order='desc', limit=50
)

# Losers
run_screener(
  market='china', sort_by='change',
  sort_order='asc', limit=50
)

# Active stocks (most active by volume)
run_screener(
  market='china', sort_by='volume',
  sort_order='desc', limit=50
)

# Unusual volume
run_screener(
  market='china', filter_preset='breakout_with_volume',
  limit=50
)
```

### Step 3: Sector Classification Analysis

Classify gainer stocks by industry/sector, calculate:
- Percentage of each sector in gainers
- Average gains of each sector (1W/1M/3M dimensions)
- Sector leader identification

### Step 4: Sector Strength Ranking

Compare multi-period returns of various sectors through performance data:

| Sector | 1W | 1M | 3M | 6M | Trend Judgment |
|--------|----|----|----|----|---------------|
| ... | ... | ... | ... | ... | Acceleration/Deceleration/Reversal |

Judgment logic:
- **Accelerating up**: Short-term > medium-term > long-term returns
- **Decelerating up**: Long-term > medium-term > short-term returns
- **Reversal up**: Short-term positive, long-term negative
- **Reversal down**: Short-term negative, long-term positive

### Step 5: News Confirmation Analysis

**News Data Requirements**:
- Market-level stock news (recent 10-20 items)
- Sector-related announcements
- Policy and industry developments

**Analysis Focus**:
Analyze news for sector associations, confirm if sector strength has fundamental/policy support.

### Step 6: Sector Leader Technical Verification

For 1-2 leader stocks of each strong sector:

```
get_technicals(symbol, interval='1D')
```

Confirm if sector leader technicals support continued sector trend.

### Step 7: Generate Sector Rotation Report

```markdown
# Sector Rotation Analysis Report

## Current Strong Sectors (Ranked by Strength)
| Rank | Sector | 1W Gain | 1M Gain | Trend Stage | Leader Stock |
|------|--------|---------|---------|------------|-------------|

## Weak Sectors
| Rank | Sector | 1W Loss | Trend Stage | Oversold? |
|------|--------|---------|------------|-----------|

## Rotation Trend Judgment
- Current market style: [Value/Growth/Cyclical/Defensive]
- Capital flow: [From XX sector to XX sector]
- Rotation stage: [Early/Middle/Late]

## Investment Recommendations
- Recommended sectors: ...
- Avoid sectors: ...
- Leader stock recommendations: ...
```

## ETF/Index Sector Analysis

Can also use index and ETF data for sector analysis:

```
# Industry index comparison
run_screener(market='america', symbol_types=['index'], sort_by='change', sort_order='desc')

# ETF sector comparison
analyze_sector_tool(sector_name='Technology', market='america', metric='perf')
analyze_sector_tool(sector_name='Healthcare', market='america', metric='perf')

# Batch multi-timeframe analysis for sector ETFs
analyze_multi_timeframe_batch(
  symbols=["NASDAQ:XLK", "NYSE:XLV", "NYSE:XLF", "NYSE:XLE"],
  timeframes=["1D", "1W"]
)
```
