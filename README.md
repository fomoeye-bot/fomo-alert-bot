# Fomo Eye

<p align="center">
  <img src="assets/fomo-eye-logo.png" alt="Fomo Eye logo" width="240">
</p>

**Telegram trader and token alerts for fomo app users.**

Set a target for a token and receive a Telegram notification when its market cap reaches that level. Follow the tokens you care about without keeping their charts open.

The latest testing build also detects DEX Screener boosts and ads for tokens with active alerts. Promotion notifications are included on Free and link directly to the token in fomo, where users can buy or sell.

Trader notifications are now in testing. Find a trader by handle, choose which trades to follow and filter by trade size and token market cap. The copy-trading interface supports saved fixed-amount setups; wallet connection and automatic execution are still under development.

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The testing build uses DEX Screener for market data and the independent fomoapi.io service for trader data. This is not an official fomo integration.

**Status: MVP in testing.**

[Open Fomo Eye in Telegram](https://t.me/fomo_eye_bot) · [Product updates](CHANGELOG.md) · [Roadmap](ROADMAP.md)

[Follow us on X for updates and new features](https://x.com/fomo_eye).

## What the MVP does

- **Find a trader:** search by fomo handle or profile link and open their card. Unavailable profile metrics are left unreported.
- **Trader notifications:** choose first observed entries, all buys, or buys and sells. Set a minimum trade size and a market-cap range, then edit or stop notifications from the trader list.
- **Copy setup:** save a fixed USD amount per trader and configure trade limits. Setups remain inactive until wallet signing and execution are connected.
- **Market-cap targets:** enter a value such as $1.5m. Fomo Eye determines whether the target requires a rise or a fall.
- **fomo token links:** paste a fomo.family token link from any menu or setup step to enter a market-cap target directly.
- **Boost and ad notifications:** automatically watch DEX Screener's latest promotion lists for tokens with active alerts, on Free and Plus. Promotion notifications keep the market-cap alert running.
- **Quick Check:** view a token’s price, market cap, FDV and liquidity, with a manual refresh option.
- **A focused alert list:** keep up to five active alerts on Free, with each target visible directly in the list. Completed alerts leave the list.
- **Plus payment flow in testing:** a one-time Telegram Stars purchase unlocks 25 active alerts for 30 days. My plan shows access, expiry and available slots. Live payment testing is still pending.
- **Open in fomo:** jump from an alert notification to the token page.

### Token alert networks

Solana · Ethereum · Base · Robinhood · BNB Chain · Arbitrum · Polygon · Avalanche · Optimism

Market data comes from DEX Screener. Token availability depends on its coverage. Monitoring currently runs on a one-minute schedule, so a brief move between checks can be missed.

The latest boost and ad lists are checked every 30 seconds through shared requests. The first snapshot is saved silently, and previously observed promotions are not announced again after a restart. These limited lists do not guarantee detection of every promotion. Boost snapshots without a unique event identifier are handled conservatively to avoid repeat notifications.

Trader notifications use one shared feed connection, with local filtering and duplicate suppression. Coverage and delays depend on the provider. First-buy detection uses a current holdings snapshot and observed entries; it cannot establish a trader's first-ever purchase from incomplete lifetime history. Notifications with market-cap filters are skipped when a fresh market cap is unavailable. Events from a disconnected interval may be missed.

## Operator tools

An owner-only Telegram statistics view shows user profiles, active token alert targets, trader subscriptions and feed status. Access is restricted to a configured Telegram user ID. User details and operational data stay outside this repository.

## Development progress

The current MVP is being tested in Telegram. Internal validation covers target conditions, trader filters, navigation, alert delivery, access controls, request budgets, promotion detection and payment handling. Both promotion endpoints and trader search have returned data in live read-only checks. The trader WebSocket also connected successfully and supplied its welcome message and replay records. Sustained live trader delivery still needs testing. Payment and trade-accounting checks use simulated data; live checkout and trading execution are not validated.

A simulated workload of 100 users with five distinct tokens each on one network required 17 market-data requests per monitoring cycle. This is a test result, not a count of live users or a production reliability claim.

- [Product updates](CHANGELOG.md)
- [Roadmap](ROADMAP.md)
- [Report a problem or suggest an improvement](https://github.com/fomoeye-bot/fomo-alert-bot/issues)

## About this repository

This is the public product overview and development log for Fomo Eye. Application source code and operational data are not published here.
