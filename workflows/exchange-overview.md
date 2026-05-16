---
description: Exchange Overview Workflow - View exchange information and market configuration
---

# Exchange Overview Workflow

View exchange and market information using tvremix tools. Unlike the previous RapidAPI TradingView approach, tvremix does not have a standalone metadata endpoint — market names and exchanges are used directly in other tool calls.

## Execution Steps

### Step 1: Determine Query Type

Determine query type based on user needs:
- **Markets**: View available market names for screeners
- **Symbols**: Search for specific trading instruments
- **Sectors**: Browse sectors and industries
- **Screener**: Explore markets with filters and sorting

> **Note**: tvremix does not have a dedicated `get_metadata` endpoint. Market names (e.g. 'america', 'china', 'japan') are used directly in `run_screener` and other tool calls. Exchanges are part of the symbol format (EXCHANGE:SYMBOL, e.g. NASDAQ:AAPL, SSE:688118).

### Step 2: Use Available Tools to Explore Markets

**Market Names** — used directly in `run_screener` and other tools:
```
Market names (used as-is in tool parameters):
- North America: 'america', 'canada'
- Europe: 'uk', 'germany', 'france'
- Asia: 'china', 'japan', 'korea', 'india'
- Others: 'australia', 'brazil', etc.
```

**Symbol Search** — discover trading instruments:
```
search_symbols(query, limit)
- query: Search keywords (required)
- limit: Number of results (default 10, max 50)
- exclude_types: Optional filter to exclude result types (e.g. ['index', 'fundamental'])
```

**Screener** — explore markets with filters:
```
run_screener(market, filters, sort_by, sort_order, limit)
- market: Market name (required, e.g. 'america', 'china')
- filters: Filter parameters (optional)
- sort_by: Sort column (default 'volume')
- sort_order: 'asc' or 'desc' (default 'desc')
- limit: Number of results (default 50)
- symbol_types: Optional list, e.g. ['stock', 'index', 'etf']
```

**Sector Analysis** — browse sectors and industries:
```
analyze_sector_tool(sector_name, market, metric, limit)
- sector_name: Sector to analyze (required)
- market: Market name (default 'america')
- metric: Ranking metric, e.g. 'market_cap', 'perf' (default 'market_cap')
- limit: Number of results (default 25)
```

### Step 3: Format Output

Format output based on query type:

**Exchange Information** (via symbol format):
- Stock exchanges: NASDAQ, NYSE, HKEX, SSE, SZSE, TSE, LSE, etc.
- Cryptocurrency exchanges: Binance, Coinbase, Kraken, OKX, Bybit, etc.
- Symbol format: EXCHANGE:SYMBOL (e.g. NASDAQ:AAPL, BINANCE:BTCUSDT)

**Market Codes**:
- North America: america, canada
- Europe: uk, germany, france
- Asia: china, japan, korea, india
- Others: australia, brazil, etc.

### Step 4: Provide Usage Guidance

Guide users on how to use the obtained information:
- How to use market names to query screeners
- How to use exchange prefixes to search symbols
- How to use `analyze_sector_tool` to browse sectors

## Example Conversations

**User**: "Which exchanges does TradingView support?"

**Execution**:
1. Explain that tvremix uses EXCHANGE:SYMBOL format — exchanges are embedded in symbol codes
2. Use `search_symbols(query='AAPL')` to demonstrate how exchanges appear in results
3. Note common exchanges: NASDAQ, NYSE, HKEX, SSE, SZSE, Binance, etc.

---

**User**: "What leaderboards are available for US stocks?"

**Execution**:
1. Use `run_screener(market='america', sort_by='volume', limit=20)` to explore US stocks
2. Explain that tvremix uses filter/sort parameters instead of tabs
3. Show how different sort_by values ('volume', 'change', 'market_cap') provide different leaderboard views

---

**User**: "Which countries' stock markets are supported?"

**Execution**:
1. List common market names used in tvremix: 'america', 'china', 'japan', 'korea', 'uk', 'germany', 'france', 'india', 'australia', etc.
2. Explain that market names are used directly in `run_screener` calls
3. Demonstrate with `run_screener(market='china', limit=10)`

---

**User**: "What data columns can be displayed on leaderboards?"

**Execution**:
1. Explain that tvremix's `run_screener` uses sort_by and filters instead of columnsets
2. Common sort_by options: 'volume', 'change', 'market_cap', 'price_earnings', 'dividend_yield', etc.
3. For individual stock data, use `get_financials(symbol)` for fundamental metrics and `get_technicals(symbol, interval='1D')` for technicals
4. Demonstrate with `run_screener(market='america', sort_by='price_earnings', limit=20)`
