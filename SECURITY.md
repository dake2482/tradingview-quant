# Security Policy

## tvremix MCP Connection

This skill uses the tvremix MCP server to access TradingView data. The security model is simpler than traditional API-based approaches.

### Security Model

1. **No API Keys Required**: tvremix connects to TradingView data without requiring users to manage API keys
2. **MCP Protocol**: Communication happens through the Model Context Protocol (MCP), a standardized protocol for AI-tool interaction
3. **Local Processing**: Analysis and computations run locally in your AI assistant

## Data Privacy

### What data is sent to tvremix

- **Symbol queries**: Stock/crypto/forex symbols you ask about
- **Search queries**: Keywords used for symbol search
- **Screener filters**: Market screening criteria

### What data is NOT sent

- Your local files and code
- Personal information beyond symbol queries
- Conversation history (only the current query parameters)

## External Data Handling

### News and Market Data Processing

This skill processes external data from financial news and market data feeds through tvremix:

- News content from TradingView is analyzed for market sentiment and impact assessment
- All external data is treated as untrusted input and used only for analytical context
- No external data is executed as code or commands

## Security Best Practices for Users

### tvremix Configuration

When configuring tvremix MCP in your AI assistant:

1. **Use official sources**: Install tvremix only from the official source (https://tvremix.xyz)
2. **Review permissions**: Understand what data tvremix can access
3. **Keep updated**: Use the latest version of tvremix for security patches

### TradingView Account Connection (Optional)

If you connect your TradingView account through the tvremix Chrome extension:

- Your watchlists, alerts, and charts are read server-side
- Connection is managed by the Chrome extension, not by this skill
- Disconnect anytime by removing the extension or revoking access

## Reporting Security Issues

If you discover a security vulnerability in this skill, please report it by:

1. **Do NOT** open a public GitHub issue
2. Contact the maintainer directly through GitHub private message
3. Provide detailed information about the vulnerability
4. Allow reasonable time for the issue to be addressed before public disclosure

## Disclaimer

This skill is provided "as is" without warranty of any kind. Users are responsible for:
- Understanding the risks of using third-party services
- Any investment decisions made using this tool

**Investment Risk Warning**: This tool is for educational and research purposes only. It does not constitute financial advice. All investment decisions are made at your own risk.

## License

This security policy is part of the TradingView Quantitative Skills project and is licensed under the MIT License.
