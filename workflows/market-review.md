---
description: Market Review Workflow - Daily market analysis and investment opportunity discovery
---

# Market Review Workflow

Daily market review, tracking hot sectors and capital flows, discovering investment opportunities.

## Execution Steps

### Step 1: Select Market

tvremix uses market names directly (e.g., 'china', 'america') — no separate metadata call needed.

### Step 2: Get Gainers/Losers Data

Call in parallel to get multi-dimensional data:

```
# Gainers
run_screener(
  market='china', sort_by='change', sort_order='desc', limit=50
)

# Losers
run_screener(
  market='china', sort_by='change', sort_order='asc', limit=50
)

# Most active (highest volume)
run_screener(
  market='china', sort_by='volume', sort_order='desc', limit=30
)

# Unusual volume
run_screener(
  market='china', filter_preset='unusual_volume', limit=30
)
```

### Step 3: Market News Analysis

**News Data Requirements**:
- Market-level stock news (recent 10-20 items)
- Country/region filter
- Language preference

**Analysis Focus**:
- Major market-moving events
- Policy announcements
- Industry trends
- Market sentiment indicators

For important news, analyze full content details for deeper context. Use `get_news(symbol, limit)` for symbol-specific news.

### Step 4: Get Index Quotes (Optional)

```
get_quotes_batch(
  symbols=["SSE:000001", "SZSE:399001", "SZSE:399006"]  # Shanghai/Shenzhen/ChiNext
)
```

### Step 5: Identify Hot Sectors

Analyze industry distribution in gainers list:
- Categorize top 50 gainers by industry
- Count number and average gain for each industry
- Identify top 3-5 sectors with highest representation

### Step 6: Analyze Capital Flow

Analyze through volume data:
- Industry distribution of active and unusual volume stocks
- Volume comparison between gainers vs losers
- Stocks with volume surge and price increase (capital inflow signal)

### Step 7: Correlate News with Market Action

Correlate companies/industries in news with gainers/losers:
- News catalysts for limit-up stocks
- Policy/event drivers for sector movements
- Sustainability assessment

### Step 8: Generate Review Report

```markdown
# [Market] Market Review - YYYY-MM-DD

## Market Overview
- Index performance: [Shanghai/Shenzhen/ChiNext changes]
- Advance/decline: XX up / XX down
- Trading volume: XX billion (vs previous +/-XX%)

## Hot Sectors (Ranked by strength)
| Rank | Sector | Gain | Representative Stocks | Catalyst |
|------|--------|------|----------------------|----------|

## Top 10 Gainers
| Rank | Stock | Gain | Volume | Unusual Signal |
|------|-------|------|--------|----------------|

## Capital Flow
- Main inflow sectors: ...
- Main outflow sectors: ...
- Unusual volume stocks: ...

## News Highlights
1. [News title] - [Impact analysis]
2. ...

## Investment Opportunities
- [Opportunity 1]: Reason and recommended stocks
- [Opportunity 2]: ...

## Risk Warnings
- [Risk 1]
- [Risk 2]
```

## Example

**User**: "How was the A-share market today?"

**Execution**:
1. Use market='china' directly (no metadata call needed)
2. `run_screener` x 4 (gainers/losers/active/unusual-volume variants)
3. `get_news(symbol, limit)` for key symbols + details
4. `get_quotes_batch` → Index quotes
5. Sector categorization → Hot sector identification → News correlation
6. Generate review report
