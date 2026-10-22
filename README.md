# Connect Four

A Python implementation of Connect Four against a rule-based AI opponent. The project follows a layered architecture (Domain-Service-UI) and provides both a Pygame graphical interface and a terminal interface.

## Architecture

```
Connect-Four-Game/
├── main.py                    # Entry point (selects CLI or GUI)
└── src/
    ├── domain/
    │   └── domain.py          # Board entity (2D matrix representation and ASCII rendering)
    ├── service/
    │   └── service.py         # Game engine (piece placement, win/draw detection, AI moves)
    ├── ui/
    │   ├── gui.py             # Pygame graphical interface with Tkinter dialogs
    │   └── ui.py              # Terminal interface using Texttable
    ├── tests/
    │   └── ServiceTests.py    # Unit tests for placement, win checks, and AI logic
    └── utils/
        └── exceptions.py      # Custom exceptions (FullColumn, InvalidColumn, InvalidInput)
```

## AI Decision Logic

The AI (`Service.computerMove`) selects moves in order of priority:
1. **Immediate Win**: Detects and plays any move that creates 4-in-a-row for the computer (`'O'`).
2. **Defensive Block**: Simulates the player's next turn and blocks any move that would result in a player win (`'X'`).
3. **Adjacency Heuristic**: Evaluates surrounding cells in an 8-neighborhood radius to favor clustered piece positioning.
4. **Random Move**: Falls back to selecting a random unpopulated column.

## Requirements

- Python 3.8+
- Dependencies:
  - `pygame`
  - `numpy`
  - `texttable`

Install dependencies:
```bash
pip install pygame numpy texttable
```

## Running the Game

Launch the launcher:
```bash
python main.py
```

You can select:
- `1` – **Console Mode**: Supports the standard 6x7 board or custom board dimensions ($H \ge 4$ or $W \ge 4$).
- `2` – **GUI Mode**: Standard 6x7 board with mouse hover piece preview and replay dialogs.

## Running Tests

Execute the unit test suite:
```bash
python -m unittest discover -s src/tests -p "*Tests.py"
```
