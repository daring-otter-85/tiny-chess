# tiny-chess

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/daring-otter-85/tiny-chess/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/daring-otter-85/tiny-chess/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A complete chess engine in a single Python file of 4,048 bytes. `main.py` is the lzma-packed form of the readable source in `engine.py` (produced by the kit's `makefun compress`); the grader runs `main.py` alone, standard library only. Inside: a 0x88 board with full legal move generation (castling, en passant, promotions), negamax alpha-beta search with a transposition table, iterative deepening, quiescence (captures, promotions and check evasions), late-move reductions and MVV-LVA/TT move ordering, and a tapered material + piece-square evaluation with passed-pawn bonuses and an endgame king table. The search runs to a fixed budget of 50,000 nodes per move and never reads a clock, so every run is deterministic. The driver plays the house gauntlet through the env at `MAKEFUN_ENV_URL` and verifies every chosen move against the env's legal move list before sending it.

## Run it

```sh
MAKEFUN_ENV_URL=http://127.0.0.1:8080 python3 main.py
```

Point `MAKEFUN_ENV_URL` at a tiny-chess-01 env server (the kit's `program/env/server.mjs` serves one gauntlet); the engine then plays every game of the gauntlet and exits when the env answers `done`.

---

<sub>Entered on [make.fun](https://make.fun/?ref=wfs35fam&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>
