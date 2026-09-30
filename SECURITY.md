# Security

<p align="center">
  <img src="assets/fomo-eye-logo.png" alt="Fomo Eye logo" width="240">
</p>

This page describes how Fomo Eye holds your money and what it refuses to do with
it. It is written for users rather than auditors, so it names the risks in plain
words instead of listing controls.

Fomo Eye is an independent project built for users of the [fomo app](https://fomo.family).
It is a testing build and is not open to the public.

## Your wallets

Two wallets are created for you the first time you start the bot: one for the EVM
networks and one for Solana. They belong to your Telegram account and to nothing
else. There is no pooled account and no house wallet in the middle: every buy,
sell and withdrawal happens from your own wallet, with your own balance.

Every wallet and every key is bound to one account id. A request made for one
account can only ever reach that account's wallet, because the lookup itself is
by account id rather than a check applied afterwards.

## Keys

Private keys are encrypted at rest. Each key is sealed with its own data key,
which is in turn wrapped by a root key held in a key management service. The
application database stores only ciphertext.

Decryption happens in one place: a separate signing component. Nothing else in
the system can read a key, and there is no operation anywhere in the interface
that returns one, with a single deliberate exception described below.

Every decryption and every signature is appended to a hash chained journal.
Entries cannot be edited or removed without breaking the chain, so what was
signed, for whom and when stays verifiable after the fact.

## What is checked before anything is signed

Before a transaction is signed, its plan is frozen and fingerprinted. The signing
component then reads the actual bytes that would be signed and compares them to
that plan:

- the recipient of the money is the address in the plan, and for a trade it must
  be an allow-listed venue;
- the amount in the transaction equals the amount in the plan, together with
  which asset that number is denominated in;
- the token being spent and the token being received are the ones in the plan;
- for a withdrawal the recipient is your address and the transaction calls no
  contract;
- consent for automated trading is present and current, except for withdrawals
  and transfers of your own tokens, which stay available even after you revoke
  automated trading, so that revoking it can never lock up your money.

Anything that does not match is refused, and the refusal is recorded.

## Exporting your private key

You can export your private key from the bot. This reverses an earlier decision
to never show keys, and it was made for one reason: your access to your own money
should not depend on this service being alive. With the key you can move your
funds from any ordinary wallet app, whatever happens to us.

The price is real, and the bot states it before showing anything:

- the key travels through Telegram, which is someone else's server and someone
  else's message history;
- the message deletes itself after one minute, which does not erase it from
  Telegram;
- after an export, treat that wallet as exposed for automated trading and move to
  a fresh one if you intend to keep copying trades.

## Executing the same trade twice

Every trader action has one canonical identity, derived from the event itself
rather than from when we received it. The same action delivered twice produces
one operation, one reserve and one signature.

A crash in the middle is handled the same way. If the process dies after a plan
is frozen but before signing, the operation resumes as the same operation. If it
dies after signing but before sending, a repeat returns the signature that
already exists rather than producing a second, different one. Two valid
signatures over the same intent would mean the money could leave twice. A repeat
that carries a different plan under the same key is refused outright, because
that is a disagreement rather than a retry.

## What we do not protect you from

- **Market risk.** Copying a trader means taking their losses as well as their
  gains. Nothing here reduces that.
- **The token itself.** A token can charge a transfer fee, freeze balances or be
  worthless. The bot will still buy and sell it, because that is what copying the
  trader means. It does not vet the asset for you.
- **Your own key, after you export it.** Once it is in your Telegram history it
  is outside our reach.
- **Sending to the wrong network.** There is no bridge. Coins sent to an address
  on another network cannot be recovered by anyone.

## Reporting a problem

If you find a security issue, please open an issue asking for a private contact
rather than posting details publicly:
https://github.com/fomoeye-bot/fomo-alert-bot/issues

Describe the class of problem and its impact. Please do not include a working
exploit in a public issue.
