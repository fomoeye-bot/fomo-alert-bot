# Fomo Eye

**Telegram market-cap alerts for fomo app users.**

Set a target for a token and receive a Telegram notification when its market cap reaches that level. Follow the tokens you care about without keeping their charts open.

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The current MVP uses DEX Screener for market data.

**Status: MVP in testing.**

[Open Fomo Eye in Telegram](https://t.me/fomo_eye_bot) · [Product updates](CHANGELOG.md) · [Roadmap](ROADMAP.md)

[Follow us on X for updates and new features](https://x.com/fomo_eye).

## What the MVP does

- **Market-cap targets:** enter a value such as $1.5m. Fomo Eye determines whether the target requires a rise or a fall.
- **Percentage targets:** track a change from your chosen entry market cap, such as +50% or −20%.
- **Quick Check:** view a token’s price, market cap, FDV and liquidity, with a manual refresh option.
- **A focused alert list:** keep up to five active alerts, with each target visible directly in the list. Completed alerts leave the list.
- **Open in fomo:** jump from an alert notification to the token page.

### Networks

Solana · Ethereum · Base · Robinhood · BNB Chain · Arbitrum · Polygon · Avalanche · Optimism

Market data comes from DEX Screener. Token availability depends on its coverage. Monitoring currently runs on a one-minute schedule, so a brief move between checks can be missed.

## Development progress

The current MVP is being tested in Telegram. Internal validation includes 102 automated checks covering target conditions, navigation, alert delivery, access controls and request limits.

A simulated workload of 100 users with five distinct tokens each on one network required 17 market-data requests per monitoring cycle. This is a test result, not a count of live users or a production reliability claim.

- [Product updates](CHANGELOG.md)
- [Roadmap](ROADMAP.md)
- [Report a problem or suggest an improvement](https://github.com/fomoeye-bot/fomo-alert-bot/issues)

## About this repository

This is the public product overview and development log for Fomo Eye. Application source code and operational data are not published here.
