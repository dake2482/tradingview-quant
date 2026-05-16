---
description: Real-time Market Monitor Workflow - Get and monitor real-time market quotes
---

# Real-time Market Monitor Workflow

Get and monitor real-time market quotes, including price, bid/ask, volume, and other key data.

## Execution Steps

### Step 1: Determine Monitoring Symbols

Extract list of symbols to monitor from user input:
- Single symbol: Get detailed quote
- Multiple symbols: Batch get quotes (up to 10)

### Step 2: Get Real-time Quotes

**Single Symbol**: Call `get_quote`

```
Parameter description:
- symbol: Symbol code (required, format EXCHANGE:SYMBOL, e.g. NASDAQ:AAPL)
```

**Multiple Symbols**: Call `get_quotes_batch`

```
Parameter description:
- symbols: Symbol array (required, up to 50 symbols)
```

### Step 3: Parse Quote Data

Extract key information:
- **Price data**: Current price, open, high, low, previous close
- **Change data**: Change %, change amount
- **Trading data**: Volume, turnover
- **Bid/Ask**: Bid price, ask price, bid/ask size
- **Market info**: Exchange, currency, trading status

### Step 4: Generate Quote Report

Output formatted quote report, including:
- Symbol basic information
- Real-time price and change status
- Trading activity analysis
- Bid/ask strength comparison
- Unusual volatility alerts

## Example Conversations

**User**: "Check Apple stock real-time quote"

**Execution**:
1. Call `get_quote`, symbol="NASDAQ:AAPL"
2. Return current price, change %, volume, and other data
3. Analyze bid/ask strength, provide brief commentary

---

**User**: "Monitor AAPL, TSLA, NVDA quotes simultaneously"

**Execution**:
1. Call `get_quotes_batch`, symbols=["NASDAQ:AAPL", "NASDAQ:TSLA", "NASDAQ:NVDA"]
2. Return real-time quote comparison for three stocks
3. Highlight largest change and most active trading

---

**User**: "Check BTCUSDT pre-market quote"

**Execution**:
1. Call `get_quote`, symbol="BINANCE:BTCUSDT"
2. Return current trading data
3. Compare with recent price changes
