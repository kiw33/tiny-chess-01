# tiny-chess-01

A chess engine in 4,096 bytes of Python (packed with lzma + base85; the
clear-text source is ~9.7 KB). It plays the house gauntlet through the env
at `MAKEFUN_ENV_URL`: alpha-beta search with quiescence, transposition
table, killer moves, MVV-LVA ordering, null-move pruning and check
extensions, to a fixed node budget per move (deterministic: no clock, no
unseeded randomness). Evaluation is tapered material + piece-square tables
with a bishop-pair bonus.

Run: `MAKEFUN_ENV_URL=<env> python3 main.py` (Python 3.13, stdlib only).

License: MIT (see LICENSE).
