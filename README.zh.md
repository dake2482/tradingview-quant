# TradingView 量化投资分析技能

[English](README.md) | [简体中文](README.zh.md)

[![Install with skills](https://img.shields.io/badge/install-skills-blue)](https://skills.sh/hypier/tradingview-quantitative-skills/tradingview-quantitative)
[![GitHub](https://img.shields.io/github/stars/hypier/tradingview-quantitative-skills?style=social)](https://github.com/hypier/tradingview-quantitative-skills)

基于 TradingView API 数据结构的专业量化投资分析指导系统，提供智能选股、技术形态识别、市场复盘、风险管理、事件驱动分析等专业方法论和分析框架。

## 特点

✨ **开箱即用** - 无需配置，安装即可使用
🔒 **安全可靠** - 无需 API 密钥，无外部依赖
📚 **专业方法论** - 基于真实 API 数据结构的分析框架
🎯 **实战导向** - 提供可操作的分析指导和策略建议

## 安装

一键安装此技能：

```bash
npx skills add hypier/tradingview-quantitative-skills
```

## 功能特性

- ✅ **智能选股框架** - 多因子综合评分方法论，技术面+基本面双重筛选策略
- 📊 **技术形态识别** - 经典形态识别算法，置信度评估和交易策略指导
- 📈 **市场复盘方法** - 热点板块追踪、资金流向分析框架
- 🛡️ **风险管理体系** - 仓位管理、止损止盈、波动率分析方法论
- 📰 **事件驱动分析** - 财报、政策、新闻的市场影响分析框架
- 🔍 **个股深度分析** - 多时间框架技术分析 + 基本面 + 新闻综合评估方法
- 💰 **基本面筛选** - 高股息、低估值、盈利能力筛选策略
- 🔄 **板块轮动分析** - 强势板块识别和轮动趋势分析方法

## 快速开始

### 1. 安装技能

```bash
npx skills add hypier/tradingview-quantitative-skills
```

### 2. 开始使用

直接用自然语言提问即可，例如：

- "如何从 A 股科技板块中筛选强势股？给我一个分析框架"
- "分析 BTC/USDT 需要关注哪些技术指标？"
- "如何进行市场复盘？有什么方法论？"
- "10 万资金的仓位管理策略是什么？"
- "如何分析财经新闻对市场的影响？"

## 使用示例

### 智能选股框架

```
请提供一个从 A 股科技板块筛选强势股的分析框架，包括：
- 技术面指标选择（RSI、MACD 等）
- 基本面指标选择（PE、ROE 等）
- 筛选流程和评分方法
```

### 个股分析方法

```
如何深度分析一只股票？请提供分析框架，包括：
- 多时间框架技术分析方法
- 基本面数据解读
- 新闻事件影响分析
- 买入时机判断标准
```

### 市场复盘框架

```
如何进行 A 股市场复盘？请提供分析框架，包括：
- 热点板块识别方法
- 资金流向分析
- 投资机会挖掘策略
```

### 风险管理方法

```
10 万资金的仓位管理策略是什么？请提供：
- 仓位分配原则
- 止损止盈设置方法
- 风险收益比计算
```

## 支持的市场

本技能提供以下市场的分析框架和方法论：

- 🇨🇳 **中国 A 股** - 上交所、深交所、北交所
- 🇺🇸 **美国** - 纽交所、纳斯达克
- 🇭🇰 **香港** - 港交所
- 🇯🇵 **日本** - 东京证券交易所
- 🇰🇷 **韩国** - 韩国交易所
- 🪙 **加密货币** - Binance、Coinbase、OKX 等
- 💱 **外汇** - 主要货币对
- 📦 **期货** - 商品、指数期货

完整市场列表和数据结构见 `references/api-documentation.md`。

## 常见问题

### Q: 这个技能提供实时数据吗？

**A**: 本技能提供基于 TradingView API 数据结构的分析框架和方法论指导。如需实时数据，可以：
1. 访问 https://rapidapi.com/hypier/api/tradingview-data1 获取 API 密钥
2. 参考 `references/api-examples/` 中的示例了解 API 调用方式
3. 查看 `references/api-documentation.md` 了解完整 API 文档

### Q: 如何理解 API 数据结构？

**A**:
1. 查看 `references/api-examples/` 目录下的真实 API 响应示例
2. 阅读 `references/api-documentation.md` 了解各个字段的含义
3. 参考 `references/china-a-stock-examples.md` 查看实战案例

### Q: 支持哪些技术指标？

**A**: 技术分析包含以下指标（参考 `references/technical-analysis.md`）：
- 趋势指标：SMA、EMA、MACD、ADX
- 动量指标：RSI、Stoch、CCI、Williams %R
- 成交量指标：Volume、MFI
- 支撑阻力：Pivot Points、Fibonacci
- 其他：ATR、Beta、Bollinger Bands

### Q: 如何获取历史 K 线数据？

**A**: 参考 `references/api-examples/01-price-data.txt` 查看价格数据的 API 格式：
- 支持时间周期：1/5/15/30/60/240/D/W/M
- 最多可获取 500 根 K 线
- 数据字段：open, high, low, close, volume, time

### Q: 新闻数据支持哪些语言？

**A**: 支持 19 种语言（参考 `references/api-documentation.md`），常用的有：
- `zh-Hans` - 简体中文
- `en` - 英语
- `ja` - 日语
- `ko` - 韩语

## 目录结构

```
tradingview-quantitative/
├── README.md                    # 英文版用户指南
├── README.zh.md                 # 中文版用户指南（本文件）
├── SKILL.md                     # AI 技能描述
├── SECURITY.md                  # 安全策略和最佳实践
├── references/                  # 参考资料
│   ├── api-examples/            # 真实 API 请求/响应示例（9个文件）
│   │   ├── 01-price-data.txt    # 价格/K线数据示例
│   │   ├── 02-quote-data.txt    # 实时报价示例
│   │   ├── 03-market-search.txt # 市场搜索示例
│   │   ├── 04-technical-analysis.txt # 技术分析示例
│   │   ├── 05-leaderboards.txt  # 排行榜示例
│   │   ├── 06-news.txt          # 新闻数据示例
│   │   ├── 07-metadata.txt      # 元数据示例
│   │   ├── 08-calendar.txt      # 日历事件示例
│   │   └── 09-logo.txt          # Logo 图片示例
│   ├── api-documentation.md     # 完整 API 文档和元数据字典
│   ├── technical-analysis.md    # 技术分析方法论
│   ├── pattern-library.md       # 形态识别库
│   ├── risk-management.md       # 风险管理方法
│   └── china-a-stock-examples.md # A 股实战案例
└── workflows/                   # 分析工作流（15个）
    ├── smart-screening.md       # 智能选股框架
    ├── pattern-recognition.md   # 形态识别方法
    ├── market-review.md         # 市场复盘框架
    ├── risk-assessment.md       # 风险评估方法
    ├── event-analysis.md        # 事件分析框架
    ├── deep-stock-analysis.md   # 个股深度分析
    ├── fundamental-screening.md # 基本面筛选
    ├── sector-rotation.md       # 板块轮动分析
    └── ...                      # 其他工作流
```

## 高级用法

### 自定义筛选框架

参考 `workflows/smart-screening.md` 和 `workflows/fundamental-screening.md`，可以构建：
- 技术指标筛选框架（RSI、MACD、ADX 等）
- 基本面筛选框架（PE、PB、ROE、股息率等）
- 市值、成交量筛选策略
- 行业板块筛选方法

### 多市场对比分析

```
如何对比中美日三国市场？请提供分析框架
```

### 策略回测方法

结合历史 K 线数据和技术指标，可以提供策略验证的方法论指导。

## 技术支持

- **API 示例**: `references/api-examples/` - 真实 API 请求/响应示例
- **API 文档**: `references/api-documentation.md` - 完整 API 文档
- **分析方法**: `references/technical-analysis.md` - 技术分析方法论
- **实战案例**: `references/china-a-stock-examples.md` - A 股实战案例

## 获取实时数据（可选）

如需访问实时市场数据，可以：

1. **访问 RapidAPI**: https://rapidapi.com/hypier/api/tradingview-data1
2. **查看 API 文档**: https://www.tradingviewapi.com
3. **参考示例**: `references/api-examples/` 目录下的真实 API 调用示例

## 免责声明

本工具提供的分析框架和方法论仅供学习研究使用，不构成任何投资建议。投资有风险，入市需谨慎。使用本工具提供的任何分析方法进行的投资决策，风险自负。

## 许可证

MIT License
