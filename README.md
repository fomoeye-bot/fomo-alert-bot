# Fomo Eye

<p align="center">
  <img src="assets/fomo-eye-logo.png" alt="Fomo Eye logo" width="240">
</p>

**Telegram market-cap and promotion alerts for fomo app users.**

Set a target for a token and receive a Telegram notification when its market cap reaches that level. Follow the tokens you care about without keeping their charts open.

The latest testing build also detects DEX Screener boosts and ads for tokens with active alerts. Promotion notifications are included on Free and link directly to the token in fomo, where users can buy or sell.

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The current MVP uses DEX Screener for market data.

**Status: MVP in testing.**

[Open Fomo Eye in Telegram](https://t.me/fomo_eye_bot) · [Product updates](CHANGELOG.md) · [Roadmap](ROADMAP.md)

[Follow us on X for updates and new features](https://x.com/fomo_eye).

## What the MVP does

- **Market-cap targets:** enter a value such as $1.5m. Fomo Eye determines whether the target requires a rise or a fall.
- **fomo token links:** paste a fomo.family token link from any menu or setup step to enter a market-cap target directly.
- **Boost and ad notifications:** automatically watch DEX Screener's latest promotion lists for tokens with active alerts, on Free and Plus. Promotion notifications keep the market-cap alert running.
- **Quick Check:** view a token’s price, market cap, FDV and liquidity, with a manual refresh option.
- **A focused alert list:** keep up to five active alerts on Free, with each target visible directly in the list. Completed alerts leave the list.
- **Plus payment flow in testing:** a one-time Telegram Stars purchase unlocks 25 active alerts for 30 days. My plan shows access, expiry and available slots. Live payment testing is still pending.
- **Open in fomo:** jump from an alert notification to the token page.

### Networks

Solana · Ethereum · Base · Robinhood · BNB Chain · Arbitrum · Polygon · Avalanche · Optimism

Market data comes from DEX Screener. Token availability depends on its coverage. Monitoring currently runs on a one-minute schedule, so a brief move between checks can be missed.

The latest boost and ad lists are checked every 30 seconds through shared requests. The first snapshot is saved silently, and previously observed promotions are not announced again after a restart. These limited lists do not guarantee detection of every promotion. Boost snapshots without a unique event identifier are handled conservatively to avoid repeat notifications.

## Operator tools

An owner-only Telegram statistics view shows user profiles and active token alert targets. Access is restricted to a configured Telegram user ID. User details and operational data stay outside this repository.

## Development progress

The current MVP is being tested in Telegram. Internal validation includes 153 automated checks covering target conditions, navigation, alert delivery, access controls, request limits, promotion detection and payment handling. Both promotion endpoints have also returned valid records during a live read-only check. Payment checks use simulated Telegram responses; live checkout validation is still pending.

A simulated workload of 100 users with five distinct tokens each on one network required 17 market-data requests per monitoring cycle. This is a test result, not a count of live users or a production reliability claim.

- [Product updates](CHANGELOG.md)
- [Roadmap](ROADMAP.md)
- [Report a problem or suggest an improvement](https://github.com/fomoeye-bot/fomo-alert-bot/issues)

## About this repository

This is the public product overview and development log for Fomo Eye. Application source code and operational data are not published here.
