[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gmlokie/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gmlokie/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Built for the make.fun bounty [tiny-chess-01](https://make.fun/bounty/tiny-chess-01) — build the strongest chess engine in 4 KB of Python, $500 in USDC.

# tiny-chess-v2 — golfed surgical book

A compact chess engine in a single 4 KB Python file, built for the
make.fun tiny-chess-01 competition. Plays through the competition
environment protocol (HTTP driver) and searches with:

- 0x88 board, Zobrist hashing, transposition table kept across moves
- Negamax with alpha-beta, PVS, aspiration windows, iterative deepening
- Null-move pruning, history-aware late move reductions, check extensions
- Quiescence search over captures and check evasions, with delta pruning
- Killers + butterfly history move ordering, MVV-LVA captures
- Evaluation: material, piece-square tables, bishop pair, tempo,
  king safety with pawn shelter, passed pawns, rook open files,
  endgame king centralisation
- Surgical opening book (4 critical moves only, Zobrist-keyed):
  Slav a2a4, e2e4, ERS-black d5b4 and c8g4

## Trial results (18-game live harness, pooled)

Node budget 160,000/move. Packed **4,062 B** (34 B under the 4,096 B cap).

- **Pooled Elo 1809 (16W/1D/1L, spare 1,629 = 543/6)** — golfing the
  surgical book lost ZERO Elo vs the un-golfed v2 (Elo 1809, spare 532),
  no time losses. Same Elo, +11 spare per 6 games.

## Files

- `main.py` — the engine (packed, 4,062 bytes, <= 4096)
- `src.py` — the engine source (unpacked; not committed, over the file cap)
- `README.md` — this file
- `LICENSE` — MIT
- `.makefun/owner.json` — owner wallet
