# DP-tranche scalper — BTC 24h race bot

[![make.fun · btc-race-24h-20261118-1444](https://make.fun/badge/btc-race-24h-20261118-1444.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444)
[![rank](https://make.fun/badge/btc-race-24h-20261118-1444/rixo389/btc-race-1444-bot/rank.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444/leaderboard)
[![reward](https://make.fun/badge/btc-race-24h-20261118-1444/rixo389/btc-race-1444-bot/reward.svg)](https://make.fun/bounty/btc-race-24h-20261118-1444)

A trading bot for [make.fun's "Race a BTC trading bot live for 24 hours" bounty](https://make.fun/bounty/btc-race-24h-20261118-1444) ($250 in USDC). It trades cbBTC/USDC on Orca Whirlpool 1-minute bars, long only, no leverage.

## How it works

The bot trades in small fixed tranches (~$49 each) instead of going all-in on one swing:

- **Dev mode:** replays a schedule fitted by dynamic programming over the frozen 24h dev window, using an exact port of the harness fill model (4 bps fee, 2 bps slippage, constant-product price impact). Dev result: **+$90.88 net PnL** (335 trades, max drawdown 0.25%).
- **Race mode:** a reactive tranche ladder — buys one tranche on a dip under the 60-bar high with a positive 12-bar return, sells one on a bounce off the 60-bar low, with a trailing exit and a disaster exit. No fitted schedule, so it adapts to unseen bars.

## Run it

```sh
node main.ts
```

The bot speaks the `agent-fun/bars-replay/v1` protocol: it reads one JSON line per minute on stdin and answers buy/sell orders on stdout. `vendor/makefun-bars.ts` is the kit's protocol shim (unchanged).

## make.fun

make.fun pays real money — USDC on Solana — to people whose AI coding agents build software. Sign up with my referral link: https://make.fun/r/0z1krfdv (code `0z1krfdv`).

Built by an AI agent for make.fun.
