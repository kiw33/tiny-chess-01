# tiny-chess-01 build log

Engine: own 0x88 design, written in this session. Negamax alpha-beta +
quiescence (captures/promos, full evasions in check) + TT (bytes(board) key)
+ killers + MVV-LVA + null-move pruning (R=2, guarded by non-pawn material)
+ check extensions + game-history repetition scoring (positions repeating an
earlier game position score 0 in search, like the house). Eval: tapered
material + string-encoded PSTs (Michniewski) + bishop pair. Fixed node
budget per move (plies-adaptive: 150k <100 plies, 60k after), deterministic,
no clock. Packed with lzma+base85 (rules allow it). ~42k nps local.

Practice trials (kit env + scorer, local, no docker):
- v1 (30k nodes): trial-0 Elo 1099 (0W 4D 2L), wall 239s.
- v2 (100k nodes + check ext): trial-0 Elo 997 (0W 3D 3L), wall 785s.
- v3 (150k adaptive + null-move): trial-0 Elo 1099 (0W 4D 2L), wall 852s.
  (6-game noise is large; v1/v2/v3 within one game of each other.)
- v4 (+ repetition scoring): trial-0 Elo 1545 (4W 1D 1L), trial-1 Elo 1545
  (4W 1D 1L), trial-2 Elo 1279 (3W 0D 3L). Mean practice Elo 1456.
  Beats depth-2/3/4 in 9/9 games across trials. Above the 1154 practice
  floor and above the sunfish baseline's ~1365 practice mean.
  Walls: 1021s / 1063s / 1005s (6 games; final has 8, est ~1350s < 1800s).
- Perft: all 19 checks pass (startpos d4, Kiwipete, ep/promo/castling).
- Packed main.py: 4062 bytes (cap 4096). Snapshot total 6685 (cap 8192).
- /tmp was wiped mid-session (~14:58 UTC, incl. the first v4 trial run);
  engine + tooling were rebuilt byte-identical from the session transcript
  into ~/workspace/makefun/tiny-chess-01-dev/ (persistent).
