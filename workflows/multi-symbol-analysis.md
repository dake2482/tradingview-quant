---
description: Multi-Symbol Batch Analysis Workflow - Batch analyze technical and quote data for multiple symbols
---

# Multi-Symbol Batch Analysis Workflow

Batch analyze technical analysis, quote data for multiple symbols, perform horizontal comparison and comprehensive evaluation.

## Execution Steps

### Step 1: Collect Symbol List

Extract list of symbols to analyze from user input:
- Support up to 10 symbols for simultaneous analysis
- Symbol format: EXCHANGE:SYMBOL (e.g., NASDAQ:AAPL)

### Step 2: Batch Get Real-time Quotes

Call `get_quotes_batch` to get real-time quotes for all symbols (up to 50 per call):

```
Parameter description:
- symbols: Array of symbols in EXCHANGE:SYMBOL format (1-50)
```

### Step 3: Batch Get Historical Charts

Make multiple parallel `get_ohlcv()` calls to get historical data for all symbols:

```
# Call get_ohlcv in parallel for each symbol
get_ohlcv(symbol, interval='1D', count=300)  # per symbol
```

### Step 4: Get Technical Analysis

For each symbol, call `get_technicals(symbol, interval='1D')` to get technical analysis signals.
Alternatively, use `analyze_multi_timeframe_batch(symbols, timeframes=['1D'])` for batch technical analysis across multiple symbols at once.

**tvremix-specific alternative**: Use `compare_symbols_tool(symbols)` for a built-in side-by-side comparison with rankings per metric.

- Aggregate buy/sell/neutral signals
- Calculate comprehensive technical score

### Step 5: Horizontal Comparison Analysis

Compare key metrics across symbols:
- **Price change comparison**: Who gained/lost the most
- **Trading activity**: Who has the highest volume
- **Technical signal comparison**: Who has the strongest technicals
- **Volatility comparison**: Who has the highest volatility

### Step 6: Generate Comparison Report

Output comprehensive comparison report:
- Quote comparison table
- Technical score ranking
- Investment value ranking
- Risk-reward ratio comparison
- Recommended priority symbols

## Example Conversations

**User**: "Compare and analyze AAPL, MSFT, GOOGL stocks"

**Execution**:
1. Call `get_quotes_batch(symbols)` to get real-time quotes
2. Call multiple parallel `get_ohlcv(symbol, interval='1D')` to get daily chart data
3. Call `get_technicals(symbol)` individually (or `analyze_multi_timeframe_batch(symbols)`) to get technical analysis
4. Generate comparison table, highlighting best performers for each metric

---

**User**: "Batch analyze tech leader stocks"

**Execution**:
1. Confirm tech leader list (AAPL, MSFT, GOOGL, AMZN, META, NVDA, TSLA, etc.)
2. Batch get quotes and technical analysis
3. Sort by price change and technical score
4. Recommend symbols with strongest technicals

---

**User**: "Compare BTC and ETH technicals"

**Execution**:
1. Call `get_quotes_batch(symbols=["BINANCE:BTCUSDT", "BINANCE:ETHUSDT"])`
2. Call parallel `get_ohlcv(symbol)` to get historical charts
3. Get technical analysis signals individually (or use `compare_symbols_tool`)
4. Compare trend strength and overbought/oversold conditions
