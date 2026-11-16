# Crypto Wallet Safety

A practical guide to keeping hot wallets safe — written for people who
actually use them (airdrops, mints, testnets, bounty payouts), not for
people who keep everything in cold storage and never touch it.

A hot wallet is a wallet whose key lives on an internet-connected
machine. It is convenient and it is exposed. This guide is about
shrinking the damage when — not if — something goes wrong.

## Contents

| File | What it is |
| --- | --- |
| [GUIDE.md](GUIDE.md) | Key storage, wallet separation, signing checks |
| [CHECKLIST.md](CHECKLIST.md) | Copy-paste checklists for setup and for every mint/sign |

## The rules in one paragraph

Keys live in `0600` files outside git, never in chat, logs, or
screenshots. Fund a hot wallet only with what you are willing to lose.
Use a separate wallet per purpose, so one compromise does not take
everything. Before signing anything, verify the chain, the token
contract, and the decimals from the contract itself — never assume —
and convert prices with integer math, never floating point.

## License

MIT — see [LICENSE](LICENSE).
