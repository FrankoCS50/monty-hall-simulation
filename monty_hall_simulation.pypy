import random
import time
import numpy as np
import matplotlib.pyplot as plt

def monty_hall(change_door):
    doors = [0, 0, 1]  # 0: goat, 1: car
    random.shuffle(doors)
    player_choice = random.randint(0, 2)

    if not change_door:
        return doors[player_choice] == 1

    # Host opens a random door with a goat
    host_choice = random.choice([i for i in range(3) if i != player_choice and doors[i] == 0])

    # Player switches to the remaining unopened door
    player_choice = next(i for i in range(3) if i != player_choice and i != host_choice)
    return doors[player_choice] == 1

def calculate_confidence_interval(proportion, n, z=1.96):
    se = (proportion * (1 - proportion) / n) ** 0.5
    return (proportion - z * se, proportion + z * se)

# Parameters
num_simulations = 100000
random.seed(time.time())

# Run simulations
results_change = np.array([monty_hall(True) for _ in range(num_simulations)])
results_no_change = np.array([monty_hall(False) for _ in range(num_simulations)])

# Calculate win rates
wins_change = results_change.sum()
wins_no_change = results_no_change.sum()

rate_change = wins_change / num_simulations
rate_no_change = wins_no_change / num_simulations

ci_change = calculate_confidence_interval(rate_change, num_simulations)
ci_no_change = calculate_confidence_interval(rate_no_change, num_simulations)

# Print results
print(f"Cambiando Porta - Vittorie: {rate_change:.4f} (CI: {ci_change[0]:.4f}, {ci_change[1]:.4f})")
print(f"Non Cambiando Porta - Vittorie: {rate_no_change:.4f} (CI: {ci_no_change[0]:.4f}, {ci_no_change[1]:.4f})")

# Cumulative plots
cumulative_change = np.cumsum(results_change) / np.arange(1, num_simulations + 1)
cumulative_no_change = np.cumsum(results_no_change) / np.arange(1, num_simulations + 1)

plt.figure(figsize=(12, 6))

# Cumulative Results
plt.plot(cumulative_change, label='Cambiando Porta')
plt.plot(cumulative_no_change, label='Non Cambiando Porta')
plt.axhline(2/3, color='blue', linestyle='--', label='Teoria (Cambiando Porta)')
plt.axhline(1/3, color='red', linestyle='--', label='Teoria (Non Cambiando Porta)')
plt.xlabel('Numero di Simulazioni')
plt.ylabel('Percentuale di Vittorie')
plt.title('Andamento Cumulativo dei Risultati')
plt.legend()
plt.grid()
plt.show()

# Bar Plots
plt.figure(figsize=(12, 5))

plt.subplot(1, 2, 1)
plt.bar(['Vittoria', 'Sconfitta'], [wins_change, num_simulations - wins_change], color=['green', 'red'])
plt.xlabel('Risultato')
plt.ylabel('Numero di Simulazioni')
plt.title('Distribuzione dei Risultati (Cambiando Porta)')

plt.subplot(1, 2, 2)
plt.bar(['Vittoria', 'Sconfitta'], [wins_no_change, num_simulations - wins_no_change], color=['green', 'red'])
plt.xlabel('Risultato')
plt.ylabel('Numero di Simulazioni')
plt.title('Distribuzione dei Risultati (Non Cambiando Porta)')

plt.tight_layout()
plt.show()
