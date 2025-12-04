# Crypto-Watcher

## Overview
Crypto-Watcher is an automation built using Make.com that monitors cryptocurrency prices. It utilizes the CoinGecko API to fetch real-time price data and routes alerts based on price changes. Alerts are logged to Supabase and sent via Telegram notifications.

## Tools Used
- **Make.com**: For creating and managing the workflow.
- **CoinGecko API**: To retrieve live cryptocurrency prices.
- **Supabase**: For logging price changes and alerts.
- **Telegram**: For sending alert notifications.

## How It Works
1. **Webhook Trigger**: The workflow starts with a webhook trigger that initiates the process.
2. **HTTP Request to CoinGecko**: It sends a request to the CoinGecko API to get the current cryptocurrency prices.
3. **Iterator**: The prices are then passed through an iterator to handle each cryptocurrency individually.
4. **Router for Price Changes**:
   - If the price goes up, the router directs the flow to send a "price up" alert via Telegram and logs the event in Supabase.
   - If the price goes down, it sends a "price down" alert and also logs that event in Supabase.
5. **Supabase Logging**: Supabase is used to store a record of all price changes and alerts.
6. **Telegram Notification**: Alerts are sent to a specified Telegram channel for immediate notification.

## Future Improvements
- Allow users to set custom alert thresholds.
- Add support for additional cryptocurrencies or data sources.
