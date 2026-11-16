# tiny-chess-01 v02

A chess engine in under 4 KB of Python, written for make.fun's
tiny-chess-01 competition. Second entry; a stronger, genuinely distinct
variant of v01.

0x88 board, negamax alpha-beta with quiescence (check extension, delta
pruning), transposition table, MVV-LVA + killer + history ordering, and
repetition detection. Evaluation: material + piece-square tables with a
tapered endgame king table, bishop-pair bonus, passed-pawn bonus (scaled
by game phase), and rook bonuses (7th rank, open/semi-open files). Fixed
node budget per move (100,000 nodes), so play is fully deterministic: no
clock, no unseeded randomness.

`main.py` is the whole engine: Python 3.13 standard library only, it
talks to the trial env over HTTP and calls no model.

Local practice Elo (3 trials, packed main.py): 1191 / 1545 / 1279,
mean 1338 — above v01's 1278, below the sunfish baseline ~1365.
