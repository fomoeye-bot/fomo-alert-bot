# Roadmap

<p align="center">
  <img src="assets/fomo-eye-logo.png" alt="Fomo Eye logo" width="240">
</p>

Fomo Eye is currently an MVP in testing. This roadmap describes priorities; dates and release scope will be announced when confirmed.

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The current MVP uses DEX Screener for market data.

## Current focus

### Validate trader notifications

Test handle lookup, notification filters and delivery from the shared trader feed. Check reconnect behavior and provider coverage during sustained operation. First-entry detection must distinguish observed additions from new entries and make gaps in available data clear.

### Finish the copy trading money paths

Wallets, signing and swap execution are connected on all five copy trading networks, and buying, selling, withdrawals and token transfers have each been carried out with real funds. What remains is the unhappy half of every path: what a user sees when a node is down, a token cannot be routed, or a transaction is sent but not yet confirmed. Each of those has to say what happened to the money, not only that something failed.

### Turn fixed trading limits into settings

Trade size, total spend and which trader actions are copied exist today as fixed values. They become settings the user owns, with defaults that are safe on their own.

### Decide how the service charges for copying

No fee model is implemented. It has to be decided before opening to users, because a fee has to be built into the same path that signs a trade rather than bolted on afterwards.

### Validate promotion notifications

Check delivery of DEX Screener boost and ad notifications for tokens with active alerts. The implementation is included on Free, with shared polling and persistent duplicate suppression. Both feed endpoints have passed an initial live read-only check; sustained monitoring and delivery still need observation on the running server.

### Validate Plus payments

Test the complete Telegram Stars checkout for 30-day Plus access, including continuation of alert setup and plan expiry. Automated payment checks are complete; live checkout and final launch pricing remain to be confirmed.

### Validate the alert experience

Check the complete flow from adding a token to receiving an alert, including target changes, completed alerts and stale buttons. Continue collecting feedback from hands-on testing.

### Validate sustained operation

Observe monitoring, copying and notification delivery over a defined test period. Check recovery after restarts and temporary service failures before expanding access. An outside health check now runs on a schedule and reports when the bot stops answering, a wallet runs low on the coin that pays fees, notifications back up or a backup goes stale.

## Next

### Prepare pilot access

Agree the pilot audience, publish the Telegram entry point when ready and give testers a clear way to report problems.

### Learn from pilot usage

Measure actual use and delivery outcomes. Use observed problems and feedback to select the next improvements.

## Planned integration direction

Pursue official fomo API access to bring the bot closer to the fomo app experience. Confirm available data, wallet authorization and trading capabilities with the fomo team before defining implementation scope. No direct fomo API integration is live in the current MVP.

## Under consideration

- Pause and resume active alerts.
- Faster ways to adjust an existing target.

These items are candidates, not scheduled commitments. Implementation details and internal security work are kept out of the public roadmap.

## Known limitations we intend to remove

- Coins sent to an address on another network cannot be recovered. We warn, and we cannot undo.
- Positions show what you hold now. Results over time are recorded internally and not yet shown.
- Rent stays locked in Solana token accounts left behind after a transfer, because reclaiming it needs an account close that the signing component does not perform yet.
