# Minimax with Alpha-Beta Pruning

Implements the Minimax adversarial search algorithm with Alpha-Beta pruning for a two-player zero-sum game. Alpha-Beta pruning eliminates branches that cannot affect the final decision, dramatically reducing the search space.

## Overview

Minimax is the foundation of classical game AI (chess, checkers, tic-tac-toe). This project implements the full tree search with Alpha-Beta optimisation, demonstrating how pruning reduces worst-case node expansions from O(b^d) to O(b^(d/2)).

## Tech Stack

- **Language:** Python 3
- **Environment:** Jupyter Notebook

## Key Concepts

- Game tree representation (states, actions, utility)
- Minimax algorithm: maximising and minimising agents
- Alpha-Beta pruning: α (best maximiser) and β (best minimiser) bounds
- Depth-limited search and evaluation heuristics
- Node expansion comparison: Minimax vs Alpha-Beta

## Project Structure

```
ai-minimax-alpha-beta-pruning/
└── minimax_alpha_beta.ipynb    # Full implementation and analysis
```

## How to Run

```bash
pip install jupyter
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

## Environment

Developed and tested with:

- Python 3.9+
- Jupyter Notebook / JupyterLab

Install dependencies:

```bash
pip install -r requirements.txt      # if provided
# or manually: pip install numpy pandas matplotlib scikit-learn torch torchvision
```

Open notebooks in order — each notebook builds on outputs from the previous one.
