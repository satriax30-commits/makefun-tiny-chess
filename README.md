# makefun-tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/satriax30-commits/makefun-tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/satriax30-commits/makefun-tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A compact original chess engine in a single Python file. It plays the make.fun tiny-chess-01 bounty: the strongest engine that fits in 4 KB of Python, standard library only, deterministic by construction.

## How it plays

- 0x88 board, full legal move generation: castling, en passant, all four promotions, checkmate and stalemate detection, repetition and fifty-move draws scored as draws inside the search.
- Alpha-beta search with iterative deepening to a fixed node budget per move (counted nodes, never a clock), a transposition table, null-move pruning, quiescence search on captures, promotions and checks, MVV-LVA capture ordering plus killer moves.
- Evaluation: material plus piece-square tables, pawn structure (doubled and isolated pawns) and king pawn-shield, bishop pair and tempo.
- Deterministic: the search runs to a fixed node count, so a replayed trial plays the same moves move for move.

## Local practice results

Tested against the kit's practice environment (6 games per trial, vs the depth-2/3/4 and fixed-node house engines): trial-0 Elo 1451 (4 wins, 0 draws, 2 losses), trial-1 Elo 1654 (5 wins, 0 draws, 1 loss), trial-2 Elo 1451 (3 wins, 2 draws, 1 loss) — practice mean about 1519. The packed entry replays all three trials move for move. Per-move time: mean 2.39 s, max 7.95 s, inside the 10 s limit.

The readable source is `engine.py`. `main.py` is the packed entry the kit's `makefun compress` command builds from it, and it stays under the 4,096-byte cap.

## Run it

```sh
python3 main.py
```

---

<sub>Entered on [make.fun](https://make.fun/?ref=kssgyf66&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
