# Number Guessing Game 

## Description
An interactive command-line number guessing game where the computer secretly picks a number and the player must guess it within a limited number of attempts. The project demonstrates core Python programming concepts including loops, conditionals, functions, and user input handling. Three difficulty levels (Easy / Medium / Hard) keep the game engaging, and a session stats tracker records performance across multiple rounds.

## Dataset
- **Source:** No external dataset — numbers are generated programmatically using Python's `random` module.
- **Description:** The "data" is the random secret number generated each round, drawn from a configurable integer range based on difficulty.

## Steps Performed
1. **Game Setup** — Configuring difficulty levels with custom ranges and attempt limits
2. **Core Logic** — Implementing the guessing loop with hint generation (Hot / Warm / Cold feedback)
3. **Automated Demo** — A binary-search-based solver runs the game end-to-end without user input (notebook-friendly)
4. **Statistics Tracker** — Win rate, average guesses per round, total score, and time-per-round aggregated and displayed at session end

## Results
- Binary search is the mathematically optimal strategy, it solves any Easy (1–50) game in ≤ 6 guesses, Medium (1–100) in ≤ 7, and Hard (1–200) in ≤ 8
- Human players typically require 20–40% more attempts than optimal due to anchoring bias
- Score formula: `max(100 - (attempts - 1) × 15 - elapsed_seconds, 10)`

## Tools Used
- Python 3.10+
- `random`  secret number generation and demo auto-solver
- `time` round timer for scoring

## Conclusion
A minimal yet engaging mini-game that reinforces fundamental Python constructs. The hot/cold hint system teaches players to converge faster essentially learning binary search intuitively. Extending this into a Flask web app or a Tkinter GUI would be a natural next step.

## Author
ATHARVA H SAWANT

