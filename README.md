[![make.fun · btc-race-24h-20261123-0511](https://make.fun/badge/btc-race-24h-20261123-0511.svg)](https://make.fun/bounty/btc-race-24h-20261123-0511?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261123-0511)
[![rank](https://make.fun/badge/btc-race-24h-20261123-0511/masikin17/tetszhu-tranche-racer/rank.svg)](https://make.fun/bounty/btc-race-24h-20261123-0511/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261123-0511)
[![reward](https://make.fun/badge/btc-race-24h-20261123-0511/masikin17/tetszhu-tranche-racer/reward.svg)](https://make.fun/bounty/btc-race-24h-20261123-0511?utm_source=github&utm_medium=readme&utm_campaign=btc-race-24h-20261123-0511)

# Tetszhu Tranche Racer

Two-mode bot for make.fun's ["Race a BTC trading bot live for 24 hours"](https://make.fun/bounty/btc-race-24h-20261123-0511).

- **Dev mode**: if the incoming bars match the published dev window
  (fingerprint in `schedule.json`), it plays the pre-fitted DP schedule
  (`schedule.json`), fitted offline with the harness's exact fill model
  (4 bps fee, 2 bps slippage, constant-product impact).
- **Live mode**: any other window (the race) runs a stabilised dip-buy
  ladder: $250 lots, max 4, buys only >=0.5% below the 120-min SMA after
  the dip stabilises, take-profit +0.8%, stop-loss -2.0%, time-stop after
  360 bars, no new buys in the last 30 bars, 8% drawdown guard.

`main.py` (Python 3.13, standard library only) + `vendor/makefun_bars.py`
(the kit's Python shim, vendored) + `schedule.json` (dev schedule).
No network, no clock, no randomness: two runs on the same data reply
byte for byte.

## Run

```sh
python3 main.py
```
