# Product updates

## Unreleased - MVP testing

The first MVP is being tested. This entry describes the current implementation; it does not announce public availability.

### Available in the testing build

- Telegram alerts for a target market cap or a percentage change from an entry market cap.
- Network selection, including Robinhood immediately after Base.
- Quick Check with token metrics and a refresh button.
- Up to five active alerts per user.
- An Open in fomo button on alert notifications.

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
