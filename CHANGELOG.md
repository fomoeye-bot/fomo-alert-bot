# Product updates

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family). We plan to integrate directly with fomo APIs, subject to official access and supported capabilities. The current MVP uses DEX Screener for market data.

## Unreleased - MVP testing

The first MVP is being tested. This entry describes the current implementation; it does not announce public availability.

### Available in the testing build

- Telegram alerts for a target market cap or a percentage change from an entry market cap.
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
