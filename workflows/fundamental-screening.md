---
description: Fundamental Screening Workflow - Use multiple columnsets to screen value stocks
---

# Fundamental Screening Workflow

Use `run_screener` with various filter and sort parameters, combined with `get_financials` and `get_forecasts` for individual stock analysis, to screen quality stocks from a fundamental perspective.

## Execution Steps

### Step 1: Determine Screening Strategy

Determine screening strategy based on user needs:

| Strategy | Core Columnset | Key Metrics |
|----------|---------------|-------------|
| Value Investing | valuation | Low PE, Low PB, Low PS |
| High Dividend | dividends | High dividend yield, stable dividends |
| Growth Stocks | profitability + income_statement | High ROE, revenue growth |
| Financial Health | balance_sheet + cash_flow | Low debt ratio, ample cash flow |

### Step 2: Understand tvremix Market and Screening Parameters

> **Note**: tvremix does not have a standalone metadata endpoint. Market names are used directly (e.g. 'america', 'china', 'japan'). The `run_screener` tool uses filter/sort parameters instead of columnset/tab parameters.

```
# Market names used directly in run_screener:
# 'america', 'china', 'japan', 'korea', 'india', 'uk', 'germany', 'france', etc.

# Use run_screener with filter params for screening
run_screener(market, filters, sort_by, sort_order, limit)

# For individual stock fundamentals:
get_financials(symbol)    # P/E, EPS, market cap, revenue growth, sector, etc.
get_forecasts(symbol)     # Analyst price targets, ratings distribution, EPS estimates
```

### Step 3: Get Leaderboard Data (Multiple Columnsets)

Call based on strategy combination, using value investing as example:

```
# Screen for valuation (sort by PE or PB)
run_screener(
  market='china', sort_by='price_earnings',
  sort_order='asc', limit=100
)

# Screen for profitability (sort by ROE or revenue growth)
run_screener(
  market='china', sort_by='roe',
  sort_order='desc', limit=100
)

# Screen for high dividend stocks
get_dividends_calendar(market='china', limit=50)
# Or use run_screener with dividend-related sort
run_screener(
  market='china', sort_by='dividend_yield',
  sort_order='desc', limit=50
)
```

### Step 4: Cross-Filter

Cross-filter results from multiple columnsets:

**Value Investing Filter Example**:
- PE < 20 (reasonable valuation)
- PB < 3 (asset discount)
- ROE > 15% (strong profitability)
- Dividend yield > 2% (dividend protection)

**Growth Stock Filter Example**:
- Revenue YoY growth > 20%
- Net profit growth > 15%
- ROE > 20%
- Gross margin > 40%

### Step 5: Technical Validation

For top candidates (5-10), call individually:

```
get_technicals(symbol, interval='1D')
```

Filter out stocks with obviously weak technicals (e.g., RSI > 80 overbought, MACD death cross).

### Step 6: Generate Screening Report

```markdown
# Fundamental Screening Results - [Strategy Name]

## Screening Criteria
- [List all criteria]

## Qualified Stocks (Total: N)

| Rank | Stock | PE | PB | ROE | Dividend Yield | Technical Score |
|------|-------|----|----|-----|----------------|-----------------|
| 1 | ... | ... | ... | ... | ... | ... |

## Detailed Analysis (Top 5)
### 1. [Stock Name]
- Valuation: ...
- Profitability: ...
- Technical: ...
- Buy recommendation: ...
```

## Common Screening Combinations

### High Dividend Strategy
```
get_dividends_calendar(market='china') → Dividend yield ranking
Cross with run_screener(market='china', sort_by='roe', sort_order='desc') → Confirm sustainable earnings
Cross with get_financials(symbol) for each candidate → Confirm financial health
```

### Low Valuation Strategy
```
run_screener(market='china', sort_by='price_earnings', sort_order='asc') → PE/PB ranking
Cross with get_financials(symbol) for each candidate → Confirm revenue and profit
Cross with get_forecasts(symbol) for each candidate → Confirm analyst expectations
```

### Blue Chip Strategy
```
run_screener(market='china', sort_by='market_cap', sort_order='desc', limit=50) → Large-cap stocks
Filter with get_financials(symbol) → High ROE confirmation
Cross with get_dividends_calendar(market='china') → Dividend protection
```
