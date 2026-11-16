# Guide

## 1. Key storage

- **One key, one file.** Each wallet's private key lives in its own
  file, for example `~/wallets/eoa-wallet-1.txt`, with permissions
  `0600` (readable only by you). Check with `ls -l`.
- **Never in chat, logs, or screenshots.** A key that appears in a chat
  log is a key you must assume is compromised. Same for terminal output
  captured in a screenshot, a pasted error message, or a file inside a
  git repo.
- **Never in environment variables that get printed.** Do not `echo
  $PRIVATE_KEY`. Do not pass keys as command-line arguments where they
  can land in shell history or process listings — pass them via a file
  or stdin instead.
- **Never in memory notes.** If a note, a doc, or a chat contains a
  key, the key is already outside your control.
- **Rotate on exposure.** If a key appears anywhere it should not,
  assume compromise: move the funds to a fresh wallet and stop using
  the old one.
- **Seed phrases follow the same rules**, plus one more: a seed phrase
  is never typed into a website, a form, or a tool you did not
  explicitly choose. No legitimate service asks for it.

## 2. Fund only what you can spend

A hot wallet is a spending wallet, not a savings wallet.

- Fund it with only what you are willing to lose in one session — a
  mint, a test, a small trade.
- Keep the bulk of your funds in a separate wallet (ideally cold
  storage) that the hot wallet never touches.
- After a mint or a payout, sweep funds you do not need back to the
  safer wallet. Do not let balances accumulate in a hot wallet.
- Never fund a hot wallet from an exchange withdrawal directly to a
  contract interaction — fund the wallet first, then interact.

## 3. One wallet per purpose

- **Separate wallets for separate jobs:** one for mints, one for
  testnet, one for bounty payouts, one for trading. A compromise of one
  must not take the others.
- **Never reuse a wallet across a testnet and mainnet for the same
  purpose.** Testnet keys and habits leak into mainnet if the wallet is
  shared.
- **Label wallets by purpose, not by balance.** A name like
  `mint-wallet-1` tells you what it is for; a name like `main-wallet`
  tells an attacker what it is worth.
- **One account per person, per program.** For testnets and competitions
  that require one account per person, do not create multiple wallets
  to game it — that gets accounts suspended and balances forfeited.

## 4. Before you sign anything

Verify before signing. Every time, even for a transaction you have
signed a hundred times before.

### 4.1 The chain, the token, and the decimals

- **Chain:** confirm the network the wallet is on matches the network
  the transaction is for. A signature on the wrong chain can still
  move funds.
- **Token contract:** confirm the token's contract address from a
  trusted source (the project's official docs or a block explorer),
  never from a chat message or a screenshot.
- **Decimals:** read them from the token contract's `decimals()`
  function. Never assume a token has 18 decimals — some have 6, some
  have 8, some have 0. A wrong decimal assumption is the most common
  way to overpay by 1,000,000×.
- **Marketplace ABI:** confirm the marketplace contract and the exact
  function you are calling, and what each parameter means.

### 4.2 Prices: integer math only

- Convert human-readable prices to base units with **integer
  (BigInt) arithmetic only**. Never use floating point for money — it
  rounds, and rounding in the wrong direction is a loss.
- After encoding a price, **decode it back** to human-readable units
  and verify it matches exactly what you intended — same number, same
  currency. If anything is uncertain or mismatched, **stop**. Never
  guess, never silently round, never execute an unverified price.
- Zero tolerance for decimal, hex, or price-binding errors. If the
  decoded price does not match your intended price exactly, the
  transaction does not go out.

### 4.3 The transaction itself

- Read the transaction before signing: to-address, value, function,
  parameters. If the wallet shows something you did not expect, stop.
- Simulate first where the tool supports it. A simulation that fails
  is a transaction you do not send.
- One transaction at a time. Do not batch-sign a queue you have not
  read.
- Never sign a blind message (an opaque hash with no readable
  content) unless you generated it yourself and know exactly what it
  is.

## 5. After signing

- Verify the result from the transaction receipt or the on-chain state
  — not from the site's display. A site can say "success" while the
  transaction failed.
- Record the transaction hash and the outcome in your own notes.
- If a transaction behaves unexpectedly, stop and investigate before
  sending another one.

## 6. If something goes wrong

- **Key exposed:** move funds immediately to a fresh wallet, then stop
  using the old one.
- **Wrong transaction sent:** do not send a second transaction to "fix"
  it until you understand the first one. A hasty fix is usually a
  second loss.
- **Funds missing:** check the transaction history on a block explorer
  first. The chain is the source of truth — not the app, not the chat.
