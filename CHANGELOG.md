# Product updates

<p align="center">
  <img src="assets/fomo-eye-logo.png" alt="Fomo Eye logo" width="240">
</p>

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The current MVP uses DEX Screener for market data.

## Unreleased - MVP testing

The first MVP is being tested. This entry describes the current implementation; it does not announce public availability.

### Updated September 30, 2026

Copy trading executes. A trader's buy is copied by contract address from the
user's own wallet on Solana, Base, BNB Chain, Ethereum and Robinhood.

- Buy, sell, withdraw and send tokens out, each carried out with real funds on
  every one of the five networks, with the amount that arrived checked against
  the amount sent.
- No allow-list of token formats. Solana tokens on the Token-2022 standard are
  traded like any other, and a token that charges a transfer fee is traded with
  that fee rather than refused. Routes longer than one step are supported.
- Auto-sell after the trader exits, off by default and switched on by the user.
  With it off, the user is still told the trader left.
- Withdraw the network coin to any address, including everything at once, and
  send the tokens themselves to a personal wallet instead of selling them.
- Export the wallet private key from the bot, with the message removing itself
  after a minute, so access to the funds does not depend on this service.

Privy is no longer part of the design. Wallets are created by the server, keys
are encrypted at rest and decrypted only inside a separate signing component
that checks every transaction against a plan frozen before signing. See
[SECURITY.md](SECURITY.md).

Corrected during live testing, listed because it is the part a reader can weigh:

- Withdrawals in the EVM networks could never be signed, because the plan did
  not declare which asset was being spent.
- Available to withdraw showed zero on funded wallets: the fee reserve was a
  flat amount in every network instead of the fee actually being charged.
- Withdrawing everything failed on networks that charge a separate data fee.
- A transfer that had already been sent could be reported as a failure when a
  node stopped answering. Sent is no longer reported as failed.
- Positions in Solana were stored with the address lower-cased, which is not a
  valid address on that network, so they could not be sold.
- Refusals now carry a sentence in plain language next to the code, and a
  network whose node did not answer is shown as not read rather than as a zero
  balance.

### Updated September 14, 2026

Work continues on copy trading implementation and Privy wallet integration. Current development focuses on trader event verification, user consent, spending limits and reliable transaction execution. Automated trading remains under development.

### Updated September 10, 2026

- Add a trader-focused menu with Find a trader, My traders, Alerts, My wallets, Portfolio and Settings.
- Support trader lookup by handle or fomo profile link, with a visual handle example.
- Add a four-step notification setup: trade type, minimum trade size, minimum market cap and maximum market cap.
- Share a trader event stream across subscriptions, reject connection replay and suppress duplicate events.
- Require a fresh holdings snapshot for first-entry detection and fresh market-cap data for cap filters.
- Add fixed-amount copy setups and persistent risk settings. Setups remain inactive; wallet signing and automatic execution are not connected.
- Add portfolio and closed-trade views backed by a fill ledger, with fee and partial-exit accounting tested on simulated fills.
- Extend owner statistics with trader subscriptions, connection status and reported API credit balance.
- Keep token targets, free promotion notifications and Plus access available through the updated menu.

### Updated September 9, 2026

- Add automatic DEX Screener boost and ad notifications for tokens with active alerts, included on Free and Plus.
- Share two promotion feeds across users and check them every 30 seconds without changing the market-cap monitoring interval.
- Save promotion state across restarts, suppress repeated feed entries and avoid sending an initial backlog.
- Keep market-cap alerts active after promotion notifications and use a single Open in fomo button.
- Preserve existing queued notifications when updating the delivery storage.
- Update the Telegram preview, profile description and welcome message with token alerts, promotion notifications, fomo links and X updates.

- Prepare a one-time Telegram Stars payment flow for Plus: 25 active alerts for 30 days, without automatic renewal.
- Offer Plus when the Free alert limit is reached, and resume alert setup after a confirmed payment.
- Add My plan with the current plan, expiry and available alert slots.
- Preserve paid access across restarts and prevent duplicate payment notifications from extending access twice.
- Retain existing alerts after Plus expires; apply the Free limit to new alerts.
- Add payment terms and a payment support entry point. Validate checkout, renewal, expiry and refund notifications with simulated Telegram responses. Live payment testing is pending.

### Updated September 8, 2026

- Accept fomo.family token links from any menu or setup step and ask for the target market cap directly.
- Remove percentage-based alert setup and the alert-type selection step.
- Convert existing active percentage alerts to equivalent absolute market-cap targets on startup.
- Preserve alert limits, shared quote limits and stale-button protection for link-based setup.

### Available in the testing build

- Telegram alerts for an exact market-cap target.
- Direct alert setup from fomo.family token links.
- Automatic boost and ad notifications for actively tracked tokens, included on Free.
- Network selection, including Robinhood immediately after Base.
- Quick Check with token metrics and a refresh button.
- Up to five active alerts per user.
- An Open in fomo button on alert notifications.
- A "Follow us on X for updates and new features" link in the /start welcome message.

### Updated September 7, 2026

- Allow switching networks using the current network picker while entering a contract address.
- Simplify owner statistics with concise totals and clearer navigation.

- Add an owner-only /stats view with user counts, usernames, active token alerts and exact targets.
- Add paginated user cards and a refresh button.
- Record profile updates and activity timestamps from new interactions; historical usernames and arrival dates are not reconstructed.
- Add /myid and local administrator configuration. Verify access restrictions and legacy database migration.

- Clarify that Fomo Eye is built for fomo app users across the project overview and bot welcome message.
- Document plans for direct fomo API integration, subject to official access and supported capabilities.
- Shorten the X follow invitation in the bot welcome message and README.

### Refined during testing

- Enter market-cap targets directly, without choosing an above/below option.
- Show each target in My Alerts and remove completed alerts from the list.
- Number active alerts from #1 instead of showing internal record IDs.
- Simplify messages and show the remaining wait when a refresh is not yet available.

### Reliability work

- Match tokens by network and exact address.
- Prevent unavailable market-cap data from producing false drop alerts.
- Retain pending notifications across restarts and retry temporary delivery failures.
- Share market-data requests across users to reduce duplicate lookups.

A dated release entry will be added when a version is approved for release.
