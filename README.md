# tiny-chess-01

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/kiw33/tiny-chess-01/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/kiw33/tiny-chess-01/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A chess engine in 4,096 bytes of Python (packed with makefun compress; the clear-text source, engine.py, is ~9.9 KB). It plays the house gauntlet through the env at `MAKEFUN_ENV_URL`: alpha-beta search with quiescence, transposition table, killer moves, MVV-LVA ordering, null-move pruning and check extensions, to a fixed node budget per move (deterministic: no clock, no unseeded randomness). Evaluation is tapered material + piece-square tables with a bishop-pair bonus. Practice mean Elo 1456 — above the 1154 floor and the nodes-100k anchor (1392); 9/9 wins vs depth-2/3/4.

## Run it

```sh
MAKEFUN_ENV_URL=<env> python3 main.py
```

License: MIT (see LICENSE).

---

<sub>Entered on [make.fun](https://make.fun/?ref=sc95sygb&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
