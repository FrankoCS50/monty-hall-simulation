# Monty Hall Simulation

This project simulates the **Monty Hall Problem**, a famous probability puzzle based on a game show. The simulation demonstrates the advantages of changing your initial choice to win a car. It also visualizes the results with graphs.

---

## Features

- Simulates a large number of Monty Hall games.
- Compares the results of **changing the door** vs. **not changing the door**.
- Visualizes outcomes with bar charts and cumulative win rate graphs.
- Highlights why changing the door gives a 2/3 chance of winning, while sticking gives only 1/3.

---

## Understanding the Monty Hall Problem

The **Monty Hall Problem** is based on a game show where contestants must choose between three doors:
- **One door** hides a **car** (the prize).
- The other **two doors** hide **goats**.

### Rules of the Game:
1. The contestant picks one of the three doors.
2. The host, who knows what is behind each door, opens one of the other two doors, revealing a goat.
3. The contestant is then given a choice:
   - **Stick** with their original door.
   - **Switch** to the other unopened door.

### The Key Question:
**Is it better to stick with your original choice or switch to the other door?**

---

## Why Is Switching Better?

At first glance, it might seem like each door has an equal chance (50/50) after the host opens a door. However, this is incorrect because the host's action provides additional information.

### Probability Breakdown:
1. **Initial Choice**:
   - When the contestant picks a door, there is a \( \frac{1}{3} \) chance the car is behind their chosen door, and a \( \frac{2}{3} \) chance it is behind one of the other two doors.

2. **Host's Action**:
   - The host always reveals a goat from the remaining two doors. This means:
     - If the contestant’s initial choice was **wrong** (\( \frac{2}{3} \) chance), the car must be behind the other unopened door.
     - If the contestant’s initial choice was **right** (\( \frac{1}{3} \) chance), switching loses because the other unopened door has a goat.

3. **Switching Increases Your Chances**:
   - If the contestant **sticks with their original choice**, they win only when their initial choice was correct: \( \frac{1}{3} \).
   - If the contestant **switches**, they win whenever their initial choice was wrong: \( \frac{2}{3} \).

Thus, **switching doubles the probability of winning** compared to sticking with the original choice.

---

## How to Run

### Requirements
Ensure you have Python installed and the following library:
- `matplotlib`
- `numpy` (optional, for optimized simulations)

Install required libraries with:
```bash
pip install matplotlib numpy
```
### Clone this repository:
git clone https://github.com/FrankoCS50/monty-hall-simulation.git
cd monty-hall-simulation

### Run the Python script:
python monty_hall_simulation.py

### Example Console Output
- Cambiando Porta - Vittorie: 0.6667 (CI: 0.6652, 0.6682)
- Non Cambiando Porta - Vittorie: 0.3333 (CI: 0.3323, 0.3348)

### Graphs
1. Bar Chart: Shows the number of wins and losses for each strategy.
1. Cumulative Plot: Tracks the win rate as the number of games increases, demonstrating convergence to theoretical probabilities.

### Repository Contents
- monty_hall_simulation.py: The Python script for the simulation.
- README.md: Project overview and instructions.

### Key Additions:
1. **Detailed Explanation of the Problem**:
   - Step-by-step rules of the game.
   - Clarification of why switching is better using probabilities.

2. **Why It’s Counterintuitive**:
   - Many people incorrectly assume a 50/50 chance after the host opens a door. This explanation clarifies how the host’s action changes the probabilities.

### License
This project is licensed under the MIT License. Feel free to use and modify it.

### Author
Created by Franko. Feedback and contributions are welcome!