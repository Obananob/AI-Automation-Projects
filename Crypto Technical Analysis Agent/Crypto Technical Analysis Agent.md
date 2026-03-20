# Crypto Technical Analysis Agent

An n8n workflow that acts as an autonomous Technical Analysis 
agent for crypto futures trading.

## What It Does

Pulls live OHLCV (Open, High, Low, Close, Volume) candle data 
for BTC, ETH, SOL, and XRP from the Bybit API across 6 
timeframes (1m, 5m, 15m, 1H, 4H, Daily), calculates key 
technical indicators, runs AI analysis, and delivers structured 
trading signals to Slack while storing results in Supabase.

## Workflow

1. **Trigger** — Manual (dev) or Scheduled (production)
2. **Loop** — Iterates through all symbols × timeframes
3. **Bybit API** — Fetches OHLCV candle data via HTTP node
4. **Technical Indicators** — Calculates via JavaScript:
   - RSI
   - MACD
   - EMA (20/50/200)
   - Bollinger Bands
   - VWAP
5. **AI Agent** — Sends structured data to Claude API with 
custom system prompt
6. **Structured Output Parser** — Parses clean JSON response:
   - Score (-100 to +100)
   - Direction (Buy / Sell / Hold)
   - Clear reasoning
7. **Slack Notification** — Posts results to channel
8. **Supabase** — Stores all results for logging

## Tools Used

- n8n
- Bybit API
- OpenAI API
- JavaScript (Code node)
- Structured Output Parser
- Slack
- Supabase
