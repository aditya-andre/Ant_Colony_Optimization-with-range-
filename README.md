# Ant Colony Optimization (ACO) for Shortest Path with Mandatory Cities

This repository contains an implementation of **Ant Colony Optimization (ACO)** to find the shortest path between two cities in a weighted graph, with the option to specify mandatory cities that must be visited along the way. The algorithm is applied to a fixed set of cities with predefined connections, but the approach can be adapted to other graphs.

## 📁 Project Structure

- `ACO.ipynb` – Jupyter Notebook with the full implementation, including graph initialization, Floyd‑Warshall preprocessing, ACO algorithm, and visualization.

## 🗺️ Graph Description

The graph consists of 9 nodes representing cities:  

**A, B, C, D, E, F, G, H, #**  

The `#` node is a special city that can be used as a mandatory stop.  
All connections are undirected and have positive weights. The notebook uses **Floyd‑Warshall** to compute the shortest distances between every pair of nodes before running ACO.

## 🧠 Algorithm Overview

1. **Preprocessing** – Floyd‑Warshall computes the all‑pairs shortest path matrix.
2. **User Input** – The user specifies:
   - Start city
   - End city
   - Optional list of mandatory cities (comma‑separated)
3. **Ant Colony Optimization** – Each ant constructs a route from start to end, ensuring all mandatory cities are visited. The probability of moving from city `i` to city `j` depends on:
   - Pheromone level (`τ`)
   - Heuristic value (inverse of shortest distance `1/d`)
4. **Pheromone Update** – After each iteration, pheromones evaporate (rate `ρ`) and ants deposit new pheromones inversely proportional to their total path length.
5. **Result** – The best route found and its total distance are displayed, along with a convergence plot.

### ACO Parameters (tunable)

| Parameter | Value | Description |
|-----------|-------|-------------|
| `n_ants`  | 10    | Number of ants per iteration |
| `n_iter`  | 100   | Maximum number of iterations |
| `α`       | 1.0   | Pheromone influence factor |
| `β`       | 2.0   | Heuristic (distance) influence factor |
| `ρ`       | 0.5   | Pheromone evaporation rate |
| `Q`       | 1.0   | Constant for pheromone deposit |

## 🚀 How to Run

### Prerequisites

- Python 3.7+
- Jupyter Notebook (or JupyterLab / VS Code with Python extension)
- Required libraries: `numpy`, `matplotlib`

Install dependencies:

```bash
pip install numpy matplotlib
