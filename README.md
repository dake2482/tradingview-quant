# TradingView Quantitative Investment Analysis Skill

[![Install with skills](https://img.shields.io/badge/install-skills-blue)](https://skills.sh/dake2482/tradingview-quant/openclaw-tradingview-quant)
[![GitHub](https://img.shields.io/github/stars/dake2482/tradingview-quant?style=social)](https://github.com/dake2482/tradingview-quant)
[![Forked from ljsd666/openclaw-tradingview-quant](https://img.shields.io/badge/forked%20from-ljsd666%2Fopenclaw--tradingview--quant-blue)](https://github.com/ljsd666/openclaw-tradingview-quant)
[![Powered by tvremix](https://img.shields.io/badge/powered%20by-tvremix-orange)](https://tvremix.xyz)

Professional quantitative investment analysis skill powered by [tvremix MCP](https://tvremix.xyz), providing real-time market data, intelligent stock screening, technical pattern recognition, market review, risk management, and event-driven analysis.

Based on TradingView API data structures with real-time data access through the tvremix MCP server.

---

**[English](#highlights)** | **[中文](#亮点)**

---

## Highlights

- **Real-Time Data** - Powered by tvremix MCP for live TradingView data
- **No API Keys** - tvremix handles data access, no RapidAPI keys needed
- **Professional Methods** - Analysis frameworks from real API data structures
- **Advanced Analytics** - SMC, swing structure, multi-TF alignment, correlation, and more
- **Ready to Use** - Install skill + configure tvremix, start analyzing immediately

## Installation

### Step 1: Install tvremix MCP

tvremix provides real-time TradingView data through the MCP protocol. Configure it in your AI assistant:

**For Claude Code** (add to `~/.claude/settings.json`):

```json
{
  "mcpServers": {
    "plugin:tvremix:tvremix": {
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-plugin-registry", "--pluginId", "tvremix"]
    }
  }
}
```

**For other MCP-compatible AI tools**, visit [tvremix.xyz/mcp](https://tvremix.xyz/mcp) for setup instructions.

> **Note**: tvremix is a third-party service. Visit [tvremix.xyz](https://tvremix.xyz) for pricing, terms, and documentation.

### Step 2: Install This Skill

```bash
npx skills add dake2482/tradingview-quant
```

## Features

- **Smart Stock Screening** - Multi-factor scoring with `run_screener`, `rank_symbol_setups`, technical + fundamental dual filtering
- **Technical Pattern Recognition** - Classic patterns via `get_ohlcv` + `get_technicals`, plus SMC/swing analysis
- **Market Review** - Hot sector tracking with `analyze_sector_tool`, capital flow analysis
- **Risk Management** - Position sizing, stop-loss/take-profit, volatility analysis via OHLCV data
- **Event-Driven Analysis** - Earnings, economic events, dividends impact via calendar tools
- **Deep Stock Analysis** - Multi-timeframe technicals + fundamentals + news comprehensive evaluation
- **Fundamental Screening** - `get_financials` + `get_forecasts` for valuation, profitability, dividends
- **Sector Rotation** - `analyze_sector_tool` + `analyze_multi_timeframe_batch` for sector analysis
- **Multi-Symbol Comparison** - `compare_symbols_tool` + `calculate_correlation_tool` for batch analysis
- **Options Analysis** - `get_option_chain` + `get_option_expirations` for options strategies

## Quick Start

### 1. Install

```bash
npx skills add dake2482/tradingview-quant
```

### 2. Configure tvremix MCP

Add tvremix to your AI assistant's MCP server configuration (see Installation above).

### 3. Start Analyzing

Ask questions in natural language:

- "Screen strong stocks from US tech sector"
- "Analyze BTC/USDT multi-timeframe trend"
- "Compare AAPL, MSFT, GOOGL fundamentals"
- "What's the sector rotation picture in US market?"
- "Risk assessment for buying NVDA with 50k capital"

## Tool Reference

### Core Data Tools

| Tool | Purpose | Example |
|------|---------|---------|
| `get_quote` | Single symbol snapshot | `get_quote(symbol="NASDAQ:AAPL")` |
| `get_quotes_batch` | Multi-symbol quotes (max 50) | `get_quotes_batch(symbols=["NASDAQ:AAPL","NASDAQ:MSFT"])` |
| `get_ohlcv` | Historical OHLCV bars | `get_ohlcv(symbol="NASDAQ:AAPL", interval="1D", count=120)` |
| `get_technicals` | Technical indicators | `get_technicals(symbol="NASDAQ:AAPL", interval="1D")` |
| `get_full_technicals` | Multi-timeframe technicals | `get_full_technicals(symbol="NASDAQ:AAPL")` |
| `get_news` | Latest news | `get_news(symbol="NASDAQ:AAPL", limit=10)` |
| `search_symbols` | Fuzzy symbol search | `search_symbols(query="Apple")` |
| `get_financials` | Fundamental data | `get_financials(symbol="NASDAQ:AAPL")` |
| `get_forecasts` | Analyst forecasts | `get_forecasts(symbol="NASDAQ:AAPL")` |

### Screening & Analysis

| Tool | Purpose | Example |
|------|---------|---------|
| `run_screener` | Market screener | `run_screener(market="america", sort_by="volume", limit=50)` |
| `analyze_sector_tool` | Sector ranking | `analyze_sector_tool(sector_name="Technology", market="america")` |
| `analyze_multi_timeframe` | Multi-TF trend | `analyze_multi_timeframe(symbol="NASDAQ:AAPL")` |
| `analyze_smc_tool` | Smart Money Concepts | `analyze_smc_tool(symbol="NASDAQ:AAPL", interval="1D")` |
| `analyze_swing_tool` | Swing structure | `analyze_swing_tool(symbol="NASDAQ:AAPL", interval="1D")` |
| `compare_symbols_tool` | Symbol comparison | `compare_symbols_tool(symbols=["NASDAQ:AAPL","NASDAQ:MSFT"])` |
| `rank_symbol_setups` | Setup ranking | `rank_symbol_setups(symbols=[...], focus="momentum")` |
| `filter_by_indicator` | Filter by indicator | `filter_by_indicator(symbols=[...], indicator="ema200", comparator="above")` |
| `calculate_correlation_tool` | Correlation matrix | `calculate_correlation_tool(symbols=[...])` |

### Calendar Tools

| Tool | Purpose |
|------|---------|
| `get_earnings_calendar` | Upcoming earnings releases |
| `get_economic_calendar` | Macro economic events |
| `get_dividends_calendar` | Dividend payments |

### Options Tools

| Tool | Purpose |
|------|---------|
| `get_option_expirations` | Available expiration dates |
| `get_option_chain` | Option chain with IV, delta, OI |

## Supported Markets

- **US** - NYSE, NASDAQ, AMEX
- **China A-shares** - SSE, SZSE, BSE
- **Hong Kong** - HKEX
- **Japan** - TSE
- **South Korea** - KRX
- **Cryptocurrency** - Binance, Coinbase, OKX, etc.
- **Forex** - Major currency pairs
- **Futures** - Commodity, index futures

**Symbol format**: `EXCHANGE:SYMBOL` (e.g., `NASDAQ:AAPL`, `BINANCE:BTCUSDT`, `SSE:688118`)

## Usage Examples

### Smart Stock Screening

```
Screen strong US tech stocks with:
- RSI between 30-70 (healthy range)
- MACD golden cross
- Above 50-day EMA
- Sort by volume
```

### Individual Stock Deep Analysis

```
Deep analysis on NASDAQ:NVDA:
- Multi-timeframe trend (weekly/daily/hourly)
- Technical indicator status
- Fundamental data (PE, ROE, revenue growth)
- Recent news catalysts
- Risk-reward for entry
```

### Sector Rotation Analysis

```
US market sector rotation analysis:
- Rank sectors by recent performance
- Identify rotation trends
- Find sector leaders
- News confirmation
```

### Risk Management

```
Risk assessment for buying NASDAQ:TSLA with $50k capital:
- Volatility analysis (daily/annualized)
- Position sizing (Kelly formula)
- Stop-loss/take-profit levels
- Risk-reward ratio
```

## Directory Structure

```
tradingview-quant/
├── README.md                    # User guide (EN + CN)
├── SKILL.md                     # AI skill description
├── SECURITY.md                  # Security policy
├── references/                  # Reference materials
│   ├── api-examples/            # API response examples (9 files)
│   ├── api-documentation.md     # Original TradingView API reference
│   ├── api-tools-guide.md       # tvremix tool combination guide
│   ├── technical-analysis.md    # Technical analysis methodology
│   ├── pattern-library.md       # Pattern recognition library
│   ├── risk-management.md       # Risk management methods
│   ├── china-a-stock-examples.md # China A-share practical cases
│   └── us-stock-examples.md     # US stock practical cases
└── workflows/                   # Analysis workflows (15 total)
    ├── smart-screening.md       # Smart stock screening
    ├── pattern-recognition.md   # Pattern recognition
    ├── market-review.md         # Market review
    ├── risk-assessment.md       # Risk assessment
    ├── event-analysis.md        # Event analysis
    ├── deep-stock-analysis.md   # Deep stock analysis
    ├── fundamental-screening.md # Fundamental screening
    ├── sector-rotation.md       # Sector rotation
    ├── multi-timeframe-analysis.md # Multi-timeframe analysis
    ├── news-briefing.md         # News briefing
    ├── calendar-tracking.md     # Calendar tracking
    ├── symbol-search.md         # Instrument search
    ├── realtime-monitor.md      # Real-time monitoring
    ├── multi-symbol-analysis.md # Multi-symbol analysis
    └── exchange-overview.md     # Exchange overview
```

## tvremix Slash Commands

When using tvremix MCP, these slash commands are available for quick analysis:

| Command | Description |
|---------|-------------|
| `/tvremix:smc` | Smart Money Concepts analysis |
| `/tvremix:swing` | Swing trading structure |
| `/tvremix:momentum` | Momentum-based analysis |
| `/tvremix:options` | Options chain analysis |
| `/tvremix:levels` | Support/resistance levels |
| `/tvremix:confluence` | Multi-factor confluence |
| `/tvremix:chart` | Chart analysis |

## FAQ

### Q: Do I need API keys?

**A**: No. tvremix MCP handles TradingView data access. No RapidAPI keys or other credentials are required for basic usage.

### Q: How is this different from the original skill?

**A**: This fork (`dake2482/tradingview-quant`) has been updated to use tvremix MCP tools instead of the RapidAPI TradingView Data API. Benefits:
- No API key management
- Real-time data through MCP protocol
- Additional tools (SMC, swing, correlation, ranking)
- Direct integration with Claude Code and other MCP-compatible tools

### Q: What happened to the API examples?

**A**: The `references/api-examples/` directory still contains the original TradingView API response examples for understanding data structures. The actual data access now goes through tvremix MCP tools.

### Q: Which technical indicators are available?

**A**: Via `get_technicals` / `get_full_technicals`:
- Trend: SMA, EMA, MACD, ADX
- Momentum: RSI, Stoch, CCI, Williams %R
- Volume: Volume, MFI
- Support/Resistance: Pivot Points, Fibonacci
- Volatility: ATR, Bollinger Bands, Beta

### Q: Can I use my TradingView watchlists?

**A**: Yes! If you connect your TradingView account through the tvremix Chrome extension, you can access your watchlists, alerts, and charts directly via `my_watchlists`, `my_alerts`, and `my_charts` tools.

## Disclaimer

The analysis frameworks and methodologies provided by this tool are for learning and research purposes only and do not constitute any investment advice. Investing involves risks; enter the market cautiously. Any investment decisions made using the analysis methods provided by this tool are at your own risk.

## License

MIT License

---

## 亮点

- **实时数据** - 基于 tvremix MCP 获取实时 TradingView 数据
- **无需 API Key** - tvremix 处理数据访问，无需 RapidAPI 密钥
- **专业方法论** - 基于真实 API 数据结构的分析框架
- **高级分析** - SMC 智能货币、摆动结构、多周期对齐、相关性等
- **开箱即用** - 安装技能 + 配置 tvremix，立即开始分析

## 安装

### 第一步：安装 tvremix MCP

tvremix 通过 MCP 协议提供实时 TradingView 数据。在你的 AI 助手中配置：

**适用于 Claude Code**（添加到 `~/.claude/settings.json`）：

```json
{
  "mcpServers": {
    "plugin:tvremix:tvremix": {
      "command": "npx",
      "args": ["-y", "@anthropic-ai/mcp-plugin-registry", "--pluginId", "tvremix"]
    }
  }
}
```

**其他兼容 MCP 的 AI 工具**，请访问 [tvremix.xyz/mcp](https://tvremix.xyz/mcp) 获取配置说明。

> **注意**：tvremix 是第三方服务。访问 [tvremix.xyz](https://tvremix.xyz) 了解定价、条款和文档。

### 第二步：安装本技能

```bash
npx skills add dake2482/tradingview-quant
```

## 功能特性

- **智能选股** - 通过 `run_screener`、`rank_symbol_setups` 多因子评分，技术面+基本面双重筛选
- **技术形态识别** - 通过 `get_ohlcv` + `get_technicals` 识别经典形态，支持 SMC/摆动分析
- **市场复盘** - `analyze_sector_tool` 热门板块追踪、资金流向分析
- **风险管理** - 基于 OHLCV 数据的仓位管理、止损止盈、波动率分析
- **事件驱动分析** - 通过日历工具分析财报、经济事件、分红影响
- **个股深度分析** - 多周期技术分析+基本面+新闻综合评估
- **基本面筛选** - `get_financials` + `get_forecasts` 估值、盈利、分红筛选
- **板块轮动** - `analyze_sector_tool` + `analyze_multi_timeframe_batch` 板块分析
- **多标的对比** - `compare_symbols_tool` + `calculate_correlation_tool` 批量分析
- **期权分析** - `get_option_chain` + `get_option_expirations` 期权策略

## 快速上手

### 1. 安装

```bash
npx skills add dake2482/tradingview-quant
```

### 2. 配置 tvremix MCP

将 tvremix 添加到 AI 助手的 MCP 服务器配置中（参见上方安装说明）。

### 3. 开始分析

直接用自然语言提问：

- "帮我从美股科技板块筛选强势股"
- "分析 BTC/USDT 多周期趋势"
- "对比 AAPL、MSFT、GOOGL 基本面"
- "美股市场板块轮动分析"
- "5万美元买入 NVDA 的风险评估"

## 支持的市场

- **美股** - NYSE、NASDAQ、AMEX
- **A股** - 上交所、深交所、北交所
- **港股** - 港交所
- **日股** - 东京证券交易所
- **韩股** - 韩国交易所
- **加密货币** - Binance、Coinbase、OKX 等
- **外汇** - 主要货币对
- **期货** - 商品期货、指数期货

**标的格式**：`EXCHANGE:SYMBOL`（如 `NASDAQ:AAPL`、`BINANCE:BTCUSDT`、`SSE:688118`）

## 使用示例

### 智能选股

```
从美股科技板块筛选强势股：
- RSI 在 30-70 健康区间
- MACD 金叉
- 价格在 50 日 EMA 上方
- 按成交量排序
```

### 个股深度分析

```
深度分析 NASDAQ:NVDA：
- 多周期趋势（周线/日线/小时线）
- 技术指标状态
- 基本面数据（PE、ROE、营收增长）
- 近期新闻催化剂
- 入场风险收益比
```

### 板块轮动分析

```
美股板块轮动分析：
- 按近期表现排名板块
- 识别轮动趋势
- 找到板块龙头
- 新闻确认
```

### 风险管理

```
5万美元买入 NASDAQ:TSLA 的风险评估：
- 波动率分析（日/年化）
- 仓位计算（凯利公式）
- 止损/止盈位
- 风险收益比
```

## tvremix 快捷命令

使用 tvremix MCP 时，可通过以下斜杠命令快速分析：

| 命令 | 描述 |
|------|------|
| `/tvremix:smc` | Smart Money Concepts 分析 |
| `/tvremix:swing` | 摆动交易结构 |
| `/tvremix:momentum` | 动量分析 |
| `/tvremix:options` | 期权链分析 |
| `/tvremix:levels` | 支撑/阻力位 |
| `/tvremix:confluence` | 多因子共振 |
| `/tvremix:chart` | 图表分析 |

## 常见问题

### Q: 需要 API Key 吗？

**A**: 不需要。tvremix MCP 处理 TradingView 数据访问，无需 RapidAPI 密钥或其他凭证。

### Q: 与原版有什么区别？

**A**: 本 fork（`dake2482/tradingview-quant`）已更新为使用 tvremix MCP 工具替代 RapidAPI TradingView Data API。优势：
- 无需管理 API 密钥
- 通过 MCP 协议获取实时数据
- 额外工具（SMC、摆动、相关性、排名）
- 直接集成 Claude Code 和其他 MCP 兼容工具

### Q: 支持哪些技术指标？

**A**: 通过 `get_technicals` / `get_full_technicals` 可获取：
- 趋势指标：SMA、EMA、MACD、ADX
- 动量指标：RSI、Stoch、CCI、Williams %R
- 成交量指标：Volume、MFI
- 支撑阻力：Pivot Points、Fibonacci
- 波动率：ATR、Bollinger Bands、Beta

### Q: 可以使用 TradingView 自选股列表吗？

**A**: 可以！通过 tvremix Chrome 扩展连接 TradingView 账户后，可通过 `my_watchlists`、`my_alerts`、`my_charts` 工具直接访问你的自选股、提醒和图表。

## 免责声明

本工具提供的分析框架和方法论仅供学习研究参考，不构成任何投资建议。投资有风险，入市需谨慎。使用本工具提供的分析方法做出的任何投资决策，风险自担。
