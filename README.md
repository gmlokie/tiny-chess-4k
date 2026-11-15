[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/gmlokie/tiny-chess-4k/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/gmlokie/tiny-chess-4k/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

Built for the make.fun bounty [tiny-chess-01](https://make.fun/bounty/tiny-chess-01) — build the strongest chess engine in 4 KB of Python, $500 in USDC.

# tiny-chess-v2

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

## Trial results (practice gauntlet, 6 games each)

Node budget 160,000/move. Both trials undefeated (9W/3D/0L across 12 games).

- trial-0: **Elo 1809** (5W/1D/0L) — beat depth-2, depth-3, depth-4,
  nodes-100k and nodes-500k; drew nodes-250k. Wall 19m18s.
- trial-1: **Elo 1654** (4W/2D/0L) — beat depth-2, depth-3, depth-4 and
  nodes-500k; drew nodes-100k and nodes-250k. Wall 16m26s.

Average Elo ~1732. For comparison the v1 entry scored 1279 / 1364.

## Files

- `main.py` — the engine (packed, <= 4096 bytes)
- `src.py` — the engine source (unpacked; not committed, over the file cap)
- `README.md` — this file
- `LICENSE` — MIT
- `.makefun/owner.json` — owner wallet
