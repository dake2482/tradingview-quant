# TradingView Quantitative Investment Analysis Skill

[![Install with skills](https://img.shields.io/badge/install-skills-blue)](https://skills.sh/dake2482/tradingview-quant/openclaw-tradingview-quant)
[![GitHub](https://img.shields.io/github/stars/dake2482/tradingview-quant?style=social)](https://github.com/dake2482/tradingview-quant)
[![Forked from ljsd666/openclaw-tradingview-quant](https://img.shields.io/badge/forked%20from-ljsd666%2Fopenclaw--tradingview--quant-blue)](https://github.com/ljsd666/openclaw-tradingview-quant)

Professional quantitative investment analysis guidance system based on TradingView API data structures, providing intelligent stock screening, technical pattern recognition, market review, risk management, and event-driven analysis frameworks and methodologies.

基于 TradingView API 数据结构的专业量化投资分析指导系统，提供智能选股、技术形态识别、市场复盘、风险管理和事件驱动分析等框架与方法论。

---

**[English](#highlights)** | **[中文](#亮点)**

---

## Highlights

- **Ready to Use** - No configuration required, install and start using
- **Safe and Secure** - No API keys needed, no external dependencies
- **Professional Methodologies** - Analysis frameworks based on real API data structures
- **Practical Oriented** - Actionable analysis guidance and strategy recommendations

## Installation

```bash
npx skills add dake2482/tradingview-quant
```

## Features

- **Smart Stock Screening Framework** - Multi-factor comprehensive scoring methodology, dual filtering strategies for technical + fundamental aspects
- **Technical Pattern Recognition** - Classic pattern recognition algorithms, confidence assessment and trading strategy guidance
- **Market Review Methods** - Hot sector tracking, capital flow analysis frameworks
- **Risk Management System** - Position management, stop-loss/take-profit, volatility analysis methodologies
- **Event-Driven Analysis** - Market impact analysis frameworks for earnings, policies, and news
- **Deep Individual Stock Analysis** - Multi-timeframe technical analysis + fundamentals + news comprehensive evaluation methods
- **Fundamental Screening** - High dividend, low valuation, profitability screening strategies
- **Sector Rotation Analysis** - Strong sector identification and rotation trend analysis methods

## Quick Start

### 1. Install the Skill

```bash
npx skills add dake2482/tradingview-quant
```

### 2. Start Using

Just ask questions in natural language, for example:

- "How to screen strong stocks from China A-share technology sector? Give me an analysis framework"
- "What technical indicators should I focus on when analyzing BTC/USDT?"
- "How to conduct market review? What methodologies are available?"
- "What's the position management strategy for 100k capital?"
- "How to analyze the impact of financial news on the market?"

## Usage Examples

### Smart Stock Screening Framework

```
Please provide an analysis framework for screening strong stocks from China A-share technology sector, including:
- Technical indicator selection (RSI, MACD, etc.)
- Fundamental indicator selection (PE, ROE, etc.)
- Screening process and scoring methods
```

### Individual Stock Analysis Methods

```
How to conduct deep analysis on a stock? Please provide an analysis framework, including:
- Multi-timeframe technical analysis methods
- Fundamental data interpretation
- News event impact analysis
- Buy timing judgment criteria
```

### Market Review Framework

```
How to conduct China A-share market review? Please provide an analysis framework, including:
- Hot sector identification methods
- Capital flow analysis
- Investment opportunity discovery strategies
```

### Risk Management Methods

```
What's the position management strategy for 100k capital? Please provide:
- Position allocation principles
- Stop-loss/take-profit setting methods
- Risk-reward ratio calculation
```

## Supported Markets

This skill provides analysis frameworks and methodologies for the following markets:

- **China A-shares** - SSE, SZSE, BSE
- **United States** - NYSE, NASDAQ
- **Hong Kong** - HKEX
- **Japan** - TSE
- **South Korea** - KRX
- **Cryptocurrency** - Binance, Coinbase, OKX, etc.
- **Forex** - Major currency pairs
- **Futures** - Commodity, index futures

For complete market list and data structures, see `references/api-documentation.md`.

## Frequently Asked Questions

### Q: Does this skill provide real-time data?

**A**: This skill provides analysis frameworks and methodology guidance based on TradingView API data structures. For real-time data, you can:
1. Visit https://rapidapi.com/hypier/api/tradingview-data1 to get API keys
2. Refer to examples in `references/api-examples/` to understand API calling methods
3. Check `references/api-documentation.md` for complete API documentation

### Q: How to understand API data structures?

**A**:
1. Check real API response examples in `references/api-examples/` directory
2. Read `references/api-documentation.md` to understand field meanings
3. Refer to `references/china-a-stock-examples.md` for practical cases

### Q: Which technical indicators are supported?

**A**: Technical analysis includes the following indicators (refer to `references/technical-analysis.md`):
- Trend indicators: SMA, EMA, MACD, ADX
- Momentum indicators: RSI, Stoch, CCI, Williams %R
- Volume indicators: Volume, MFI
- Support resistance: Pivot Points, Fibonacci
- Others: ATR, Beta, Bollinger Bands

### Q: How to get historical K-line data?

**A**: Refer to `references/api-examples/01-price-data.txt` for price data API format:
- Supported timeframes: 1/5/15/30/60/240/D/W/M
- Maximum 500 K-lines available
- Data fields: open, high, low, close, volume, time

### Q: Which languages are supported for news data?

**A**: Supports 19 languages (refer to `references/api-documentation.md`), commonly used are:
- `zh-Hans` - Simplified Chinese
- `en` - English
- `ja` - Japanese
- `ko` - Korean

## Directory Structure

```
tradingview-quant/
├── README.md                    # User guide (EN + CN)
├── SKILL.md                     # AI skill description
├── SECURITY.md                  # Security policy and best practices
├── references/                  # Reference materials
│   ├── api-examples/            # Real API request/response examples (9 files)
│   │   ├── 01-price-data.txt    # Price/K-line data examples
│   │   ├── 02-quote-data.txt    # Real-time quote examples
│   │   ├── 03-market-search.txt # Market search examples
│   │   ├── 04-technical-analysis.txt # Technical analysis examples
│   │   ├── 05-leaderboards.txt  # Leaderboard examples
│   │   ├── 06-news.txt          # News data examples
│   │   ├── 07-metadata.txt      # Metadata examples
│   │   ├── 08-calendar.txt      # Calendar event examples
│   │   └── 09-logo.txt          # Logo image examples
│   ├── api-documentation.md     # Complete API documentation and metadata dictionary
│   ├── api-tools-guide.md       # API data structure guide
│   ├── technical-analysis.md    # Technical analysis methodology
│   ├── pattern-library.md       # Pattern recognition library
│   ├── risk-management.md       # Risk management methods
│   ├── china-a-stock-examples.md # China A-share practical cases
│   └── us-stock-examples.md     # US stock practical cases
└── workflows/                   # Analysis workflows (15 total)
    ├── smart-screening.md       # Smart stock screening framework
    ├── pattern-recognition.md   # Pattern recognition methods
    ├── market-review.md         # Market review framework
    ├── risk-assessment.md       # Risk assessment methods
    ├── event-analysis.md        # Event analysis framework
    ├── deep-stock-analysis.md   # Deep individual stock analysis
    ├── fundamental-screening.md # Fundamental screening
    ├── sector-rotation.md       # Sector rotation analysis
    ├── multi-timeframe-analysis.md # Multi-timeframe analysis
    ├── news-briefing.md         # News briefing
    ├── calendar-tracking.md     # Calendar event tracking
    ├── symbol-search.md         # Instrument search
    ├── realtime-monitor.md      # Real-time monitoring
    ├── multi-symbol-analysis.md # Multi-symbol batch analysis
    └── exchange-overview.md     # Exchange overview
```

## Advanced Usage

### Custom Screening Framework

Refer to `workflows/smart-screening.md` and `workflows/fundamental-screening.md` to build:
- Technical indicator screening frameworks (RSI, MACD, ADX, etc.)
- Fundamental screening frameworks (PE, PB, ROE, dividend yield, etc.)
- Market cap, volume screening strategies
- Industry sector screening methods

### Multi-Market Comparative Analysis

```
How to compare markets in China, US, and Japan? Please provide an analysis framework
```

### Strategy Backtesting Methods

Combining historical K-line data and technical indicators, methodology guidance for strategy validation can be provided.

## Technical Support

- **API Examples**: `references/api-examples/` - Real API request/response examples
- **API Documentation**: `references/api-documentation.md` - Complete API documentation
- **Analysis Methods**: `references/technical-analysis.md` - Technical analysis methodology
- **Practical Cases**: `references/china-a-stock-examples.md` - China A-share practical cases

## Get Real-Time Data (Optional)

To access real-time market data, you can:

1. **Visit RapidAPI**: https://rapidapi.com/hypier/api/tradingview-data1
2. **Refer to Examples**: Real API calling examples in `references/api-examples/` directory

## Disclaimer

The analysis frameworks and methodologies provided by this tool are for learning and research purposes only and do not constitute any investment advice. Investing involves risks; enter the market cautiously. Any investment decisions made using the analysis methods provided by this tool are at your own risk.

## License

MIT License

---

## 亮点

- **开箱即用** - 无需配置，安装即可使用
- **安全可靠** - 无需 API Key，无外部依赖
- **专业方法论** - 基于真实 API 数据结构的分析框架
- **实战导向** - 可操作的分析指导和策略建议

## 安装

```bash
npx skills add dake2482/tradingview-quant
```

## 功能特性

- **智能选股框架** - 多因子综合评分方法论，技术面+基本面双重筛选策略
- **技术形态识别** - 经典形态识别算法、置信度评估与交易策略指导
- **市场复盘方法** - 热门板块追踪、资金流向分析框架
- **风险管理体系** - 仓位管理、止损止盈、波动率分析方法论
- **事件驱动分析** - 财报、政策、新闻等市场影响分析框架
- **个股深度分析** - 多周期技术分析+基本面+新闻综合评估方法
- **基本面筛选** - 高股息、低估值、盈利能力筛选策略
- **板块轮动分析** - 强势板块识别与轮动趋势分析方法

## 快速上手

### 1. 安装技能

```bash
npx skills add dake2482/tradingview-quant
```

### 2. 开始使用

直接用自然语言提问即可，例如：

- "帮我从A股科技板块筛选强势股，给出分析框架"
- "分析 BTC/USDT 应该关注哪些技术指标？"
- "如何做市场复盘？有哪些方法论？"
- "10万资金怎么管理仓位？"
- "如何分析财经新闻对市场的影响？"

## 使用示例

### 智能选股框架

```
请提供从A股科技板块筛选强势股的分析框架，包括：
- 技术指标筛选（RSI、MACD 等）
- 基本面指标筛选（PE、ROE 等）
- 筛选流程与评分方法
```

### 个股分析方法

```
如何对一只股票做深度分析？请提供分析框架，包括：
- 多周期技术分析方法
- 基本面数据解读
- 新闻事件影响分析
- 买入时机判断标准
```

### 市场复盘框架

```
如何做A股市场复盘？请提供分析框架，包括：
- 热门板块识别方法
- 资金流向分析
- 投资机会发现策略
```

### 风险管理方法

```
10万资金的仓位管理策略是什么？请提供：
- 仓位分配原则
- 止损止盈设置方法
- 风险收益比计算
```

## 支持的市场

本技能提供以下市场的分析框架和方法论：

- **A股** - 上交所、深交所、北交所
- **美股** - NYSE、NASDAQ
- **港股** - 港交所
- **日股** - 东京证券交易所
- **韩股** - 韩国交易所
- **加密货币** - Binance、Coinbase、OKX 等
- **外汇** - 主要货币对
- **期货** - 商品期货、指数期货

完整市场列表和数据结构请参见 `references/api-documentation.md`。

## 常见问题

### Q: 这个技能提供实时数据吗？

**A**: 本技能提供基于 TradingView API 数据结构的分析框架和方法论指导。获取实时数据可以：
1. 访问 https://rapidapi.com/hypier/api/tradingview-data1 获取 API Key
2. 参考 `references/api-examples/` 中的示例了解 API 调用方式
3. 查看 `references/api-documentation.md` 了解完整 API 文档

### Q: 如何理解 API 数据结构？

**A**:
1. 查看 `references/api-examples/` 目录中的真实 API 响应示例
2. 阅读 `references/api-documentation.md` 了解字段含义
3. 参考 `references/china-a-stock-examples.md` 中的实战案例

### Q: 支持哪些技术指标？

**A**: 技术分析包括以下指标（详见 `references/technical-analysis.md`）：
- 趋势指标：SMA、EMA、MACD、ADX
- 动量指标：RSI、Stoch、CCI、Williams %R
- 成交量指标：Volume、MFI
- 支撑阻力：Pivot Points、Fibonacci
- 其他：ATR、Beta、Bollinger Bands

### Q: 如何获取历史K线数据？

**A**: 参考 `references/api-examples/01-price-data.txt` 了解价格数据 API 格式：
- 支持周期：1/5/15/30/60/240/D/W/M
- 最多获取 500 根K线
- 数据字段：open、high、low、close、volume、time

### Q: 新闻数据支持哪些语言？

**A**: 支持 19 种语言（详见 `references/api-documentation.md`），常用语言：
- `zh-Hans` - 简体中文
- `en` - 英文
- `ja` - 日文
- `ko` - 韩文

## 进阶用法

### 自定义选股框架

参考 `workflows/smart-screening.md` 和 `workflows/fundamental-screening.md` 构建：
- 技术指标筛选框架（RSI、MACD、ADX 等）
- 基本面筛选框架（PE、PB、ROE、股息率等）
- 市值、成交量筛选策略
- 行业板块筛选方法

### 多市场对比分析

```
如何对比中国、美国、日本三个市场？请提供分析框架
```

### 策略回测方法

结合历史K线数据和技术指标，可以提供策略验证的方法论指导。

## 免责声明

本工具提供的分析框架和方法论仅供学习研究参考，不构成任何投资建议。投资有风险，入市需谨慎。使用本工具提供的分析方法做出的任何投资决策，风险自担。
