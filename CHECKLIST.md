# Checklists

## Wallet setup

- [ ] One key per file, `0600` permissions (`ls -l` confirms)
- [ ] Key files outside any git repo
- [ ] No key in chat, logs, screenshots, or notes
- [ ] Wallets labeled by purpose (mint / testnet / payout / trading)
- [ ] Hot wallet funded only with what I am willing to lose
- [ ] Bulk funds in a separate, safer wallet
- [ ] Seed phrase stored offline, never typed into a website

## Before every mint or sign

- [ ] Chain matches the intended network
- [ ] Token contract address verified from a trusted source
- [ ] Decimals read from the contract's `decimals()` (never assumed)
- [ ] Marketplace contract and function verified
- [ ] Price converted with integer (BigInt) math — no floating point
- [ ] Encoded price decoded back and matches exactly (number + currency)
- [ ] Transaction read in full (to, value, function, parameters)
- [ ] Simulated first, where supported
- [ ] One transaction at a time; no blind signing

## After every transaction

- [ ] Result verified from the receipt / on-chain state (not the site display)
- [ ] Transaction hash recorded
- [ ] Balance checked against expectation

## If a key is exposed

- [ ] Funds moved immediately to a fresh wallet
- [ ] Old wallet stopped being used
- [ ] Exposure source noted (where did the key appear?)
- [ ] Any service that held the key notified, if relevant
