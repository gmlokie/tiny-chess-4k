# tiny-chess-01 — a 4 KB chess engine in Python

A complete chess engine packed into a single `main.py` of at most 4,096 bytes,
written in pure Python 3 standard library. It plays the make.fun
"Build the strongest chess engine in 4 KB of Python" competition
(`tiny-chess-01`) by talking HTTP to the trial harness at `$MAKEFUN_ENV_URL`.

## How it plays

- **Board:** 0x88 board, Zobrist hashing, incremental evaluation.
- **Search:** negamax with alpha-beta, iterative deepening to a fixed
  node budget (100k nodes/move), transposition table, killer moves,
  MVV-LVA capture ordering, null-move pruning (R=3), late-move reductions,
  quiescence search (captures, plus all evasions when in check).
- **Evaluation:** material + formula-generated piece-square tables,
  bishop-pair bonus, king safety/endgame king tables, tempo bonus.
- **Determinism:** fixed node budget, no clock, no unseeded randomness —
  the same position always yields the same move.

## Files

- `main.py` — the packed entrypoint (<= 4,096 bytes). The only file the
  harness runs.
- `src.py` — the readable engine source this entrypoint was packed from
  (via the kit's `makefun compress`).
- `test_fresh.py` — unit tests: perft (startpos + Kiwipete), make/unmake
  consistency, eval checks, root smoke, bench.

## Run a practice trial locally

```sh
bash run_trial0.sh trial-0
```

Starts the kit environment server, runs `python3 main.py` against it,
then scores with the kit scorer.

## Licence

MIT — see `LICENSE`.

## Results

Practice trial-0 (6 games vs depth/node anchors, Elo floor 1154):

- Trial-0 result and Elo recorded in `TRIAL0.md` after the run.
- Unit tests (`test_fresh.py`): perft exact at startpos depths 1–4
  (20 / 400 / 8902 / 197281) and Kiwipete depths 1–3
  (48 / 2039 / 97862); make/unmake restores full state over 200 random
  moves; eval symmetry and bishop-pair bonus verified.
