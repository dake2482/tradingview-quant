# tvremix MCP Tools Usage Guide

> Tool combination patterns, best practices for various analysis scenarios using tvremix MCP

---

## tvremix MCP Overview

This skill uses the tvremix MCP server to access real-time TradingView data. All tools use the following conventions:

- **Symbol format**: `EXCHANGE:SYMBOL` (e.g., `NASDAQ:AAPL`, `SSE:688118`, `BINANCE:BTCUSDT`)
- **Interval format**: `1m`, `5m`, `15m`, `30m`, `1h`, `4h`, `1D`, `1W`, `1M`

### Quick Reference: Common Markets

| Market | market parameter | Example Exchange Prefix |
|--------|-----------------|----------------------|
| US | america | NASDAQ:, NYSE:, AMEX: |
| China | china | SSE:, SZSE:, BSE: |
| Hong Kong | hongkong | HKEX: |
| Japan | japan | TSE: |
| Korea | korea | KRX: |

---

## Tool Combination Patterns

### Pattern 1: Deep Individual Stock Analysis

```
1. search_symbols(query="company name") → Get accurate symbol
2. get_quote(symbol) → Real-time price, change, volume
3. get_ohlcv(symbol, interval='1D', count=120) → Daily OHLCV data
4. get_full_technicals(symbol) → Multi-timeframe technical indicators
5. get_news(symbol, limit=10) → Related news
6. get_earnings_calendar(symbols=[symbol]) → Recent earnings dates
```

**Advanced variant**: Replace steps 3-4 with `analyze_multi_timeframe(symbol)` for built-in multi-TF analysis.

### Pattern 2: Smart Stock Screening (Technical + Fundamental)

```
1. run_screener(market='america', sort_by='change', sort_order='desc', limit=100) → Candidate pool
2. For Top candidates: get_technicals(symbol, interval='1D') → Technical verification
3. For Top candidates: get_financials(symbol) → Fundamental data
4. For Top candidates: get_ohlcv(symbol, interval='1D', count=60) → Chart verification
```

**Advanced variant**: Use `rank_symbol_setups(symbols, focus='momentum')` for automated scoring.

### Pattern 3: Multi-Timeframe Trend Confirmation

```
1. get_ohlcv(symbol, interval='1M', count=24) → Monthly trend
2. get_ohlcv(symbol, interval='1W', count=52) → Weekly trend
3. get_ohlcv(symbol, interval='1D', count=120) → Daily trend
4. get_ohlcv(symbol, interval='1h', count=120) → Hourly details
5. get_full_technicals(symbol) → Multi-period TA signals
```

**Advanced variant**: Use `analyze_multi_timeframe(symbol, timeframes=['15m','1h','4h','1D','1W'])` for one-call multi-TF alignment.

### Pattern 4: Sector Rotation Analysis

```
1. analyze_sector_tool(sector_name='Technology', market='america') → Sector ranking
2. run_screener(market='america', sort_by='change', sort_order='desc', limit=50) → Top performers
3. get_news(symbol, limit=5) → News for top sector leaders
4. analyze_multi_timeframe_batch(symbols=[...], timeframes=['1D','1W']) → Batch verification
```

### Pattern 5: Fundamental Screening

```
1. run_screener(market='america', filters=[...], limit=100) → Screen by criteria
2. For candidates: get_financials(symbol) → PE, ROE, revenue, margins
3. For candidates: get_forecasts(symbol) → Analyst consensus
4. For candidates: get_dividends_calendar(market='america') → Dividend info
```

### Pattern 6: Market Review

```
1. run_screener(market='america', sort_by='change', sort_order='desc', limit=50) → Gainers
2. run_screener(market='america', sort_by='change', sort_order='asc', limit=50) → Losers
3. run_screener(market='america', sort_by='volume', sort_order='desc', limit=30) → Active
4. get_news(symbol, limit=10) → Market news
5. For important news: get_news_story(story_id) → Full content
```

### Pattern 7: Multi-Symbol Comparison

```
1. get_quotes_batch(symbols=[...]) → Batch real-time quotes
2. compare_symbols_tool(symbols=[...]) → Side-by-side comparison
3. calculate_correlation_tool(symbols=[...]) → Correlation matrix
4. analyze_multi_timeframe_batch(symbols=[...]) → Batch multi-TF analysis
```

### Pattern 8: Risk Assessment

```
1. get_ohlcv(symbol, interval='1D', count=250) → 1-year daily data
2. get_quote(symbol) → Current price
3. get_technicals(symbol, interval='1D') → ATR, Beta, Pivot Points
4. compute_levels_batch(symbols=[symbol], methods=['swing','smc']) → Support/resistance
```

---

## Key Tool Parameters

### get_ohlcv Interval Selection

| interval | Meaning | Typical count | Use Cases |
|----------|---------|--------------|-----------|
| 1m | 1 minute | 60-240 | Intraday trading |
| 5m | 5 minutes | 48-120 | Short-term analysis |
| 15m | 15 minutes | 48-96 | Short-term analysis |
| 1h | 1 hour | 48-168 | Swing analysis |
| 4h | 4 hours | 30-90 | Swing analysis |
| 1D | Daily | 60-250 | Medium-term analysis |
| 1W | Weekly | 52-104 | Medium-long term |
| 1M | Monthly | 24-60 | Long-term trend |

### get_full_technicals Return Fields

Multi-timeframe signals across 15m/1h/4h/1D/1W with:

- **RSI(14)**: >70 overbought, <30 oversold
- **MACD**: DIF/DEA/histogram, golden cross/death cross
- **Stoch**: K/D values
- **CCI(20)**: Commodity Channel Index
- **ADX(14)**: >25 trending, >50 strong trend
- **SMA/EMA**: Multiple period moving averages
- **Bollinger Bands**: Upper/middle/lower
- **ATR**: Average True Range

### Screener Filter Presets

tvremix provides built-in filter presets for common screening:
- `breakout_with_volume` - Price breakouts with volume confirmation
- `earnings_runup` - Stocks running up before earnings
- `new_highs` - Stocks at new highs
- `oversold_healthy` - Oversold but fundamentally healthy
- `pullback_with_reversal` - Pullback showing reversal signals
- `relative_strength` - Relative strength leaders

### Calendar Tools

- `get_earnings_calendar(symbols, date_from, date_to)` — Earnings releases
- `get_economic_calendar(countries, date_from, date_to, importance)` — Macro events
- `get_dividends_calendar(date_from, date_to)` — Dividend payments

Date format: `YYYY-MM-DD` (ISO format).

---

## tvremix-Specific Advanced Tools

These tools go beyond basic data access and provide structured analysis:

| Tool | What It Does |
|------|-------------|
| `analyze_smc_tool` | Smart Money Concepts: BOS/CHoCH, order blocks, FVGs, liquidity |
| `analyze_swing_tool` | Swing structure: pivots, trendlines, channels, range zones |
| `analyze_multi_timeframe` | Multi-TF trend alignment with aggregated score |
| `analyze_multi_timeframe_batch` | Batch multi-TF for watchlist scanning |
| `compare_symbols_tool` | Side-by-side comparison with rankings |
| `rank_symbol_setups` | Score and rank symbols by setup quality |
| `filter_by_indicator` | Filter symbols by indicator relationship (above/below EMA, etc.) |
| `compute_levels_batch` | Batch compute support/resistance and SMC levels |
| `calculate_correlation_tool` | Pearson correlation matrix from real OHLCV data |
| `get_technicals_rating` | Aggregated buy/sell/neutral rating |
| `get_financials` | Fundamental data (P/E, EPS, market cap, etc.) |
| `get_forecasts` | Analyst price targets and ratings distribution |
| `web_search` | General web search for news and research |
