# Minimax with Alpha-Beta Pruning

Implements the Minimax adversarial search algorithm with Alpha-Beta pruning for a two-player zero-sum game. Alpha-Beta pruning eliminates branches that cannot affect the final decision, dramatically reducing the search space.

## Overview

Minimax is the foundation of classical game AI (chess, checkers, tic-tac-toe). This project implements the full tree search with Alpha-Beta optimisation for **multi-pile Nim**: players alternately remove one or more objects from a single pile on their turn, and the player who removes the last object wins. The notebook implements both a plain Minimax player and an Alpha-Beta-pruned player, then lets you play against either.

## Tech Stack

- **Language:** Python 3
- **Libraries:** NumPy
- **Environment:** Jupyter Notebook

## Key Concepts

- Game tree representation (states, actions, utility) for multi-pile Nim
- Minimax algorithm: maximising and minimising agents
- Alpha-Beta pruning: α (best maximiser) and β (best minimiser) bounds
- Depth-based evaluation punishment (`THETA`) to prefer faster wins
- Runtime comparison between the Minimax and Alpha-Beta Pruning implementations

## Project Structure

```
ai-minimax-alpha-beta-pruning/
└── minimax_alpha_beta.ipynb    # Full implementation and analysis
```

## How to Run

Developed and tested with Python 3.9+.

```bash
pip install numpy jupyter
jupyter notebook minimax_alpha_beta.ipynb
```

## Algorithm

```
function alphabeta(node, depth, α, β, maximisingPlayer):
    if depth == 0 or node is terminal:
        return heuristic(node)
    if maximisingPlayer:
        value = -∞
        for child in children(node):
            value = max(value, alphabeta(child, depth-1, α, β, False))
            α = max(α, value)
            if value >= β: break  # β cutoff
        return value
    else:
        value = +∞
        for child in children(node):
            value = min(value, alphabeta(child, depth-1, α, β, True))
            β = min(β, value)
            if value <= α: break  # α cutoff
        return value
```

## Results

Measured directly from the notebook's test cases:

**Test Case 1 — Minimax (no pruning), fresh state `[3, 4, 5]`:**
- Evaluation value: `-0.003043252722170458`
- AI move: `(0, 1)`
- Elapsed time: `0.4191100597381592` s

**Test Case 3 — Alpha-Beta Pruning:**
- Evaluation value: `1`
- AI move: `None`
- Elapsed time: `1.5020370483398438e-05` s

Note: Test Case 3 runs against whatever pile state is left over after Test Case 2's interactive game (which plays `[3, 4, 5]` down to an empty, terminal state), not a fresh `[3, 4, 5]` board — so these two elapsed times are not a controlled, equal-depth comparison of the two algorithms.

**Interactive games (Test Case 2 and Test Case 4):** in both recorded playthroughs, the AI won — the Minimax player took the final object to reduce `[3, 4, 5]` to empty, and the Alpha-Beta player did the same in a separate game.
