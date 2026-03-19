# UGV Static Battlefield Navigation (A* Search)

## Overview
This project simulates an Unmanned Ground Vehicle (UGV) navigating a 70x70 km static battlefield. It generates a grid with randomly placed obstacles based on a user-defined density (Low, Medium, or High). The UGV uses the **A* (A-Star) Search Algorithm** with a Manhattan distance heuristic to calculate the optimal, shortest path from the top-left corner (0,0) to the bottom-right corner (69,69) while avoiding all obstacles. 

Because the obstacles are static and known *a-priori*, the algorithm calculates the complete path before the UGV begins moving.

## Prerequisites
This code is optimized for **Google Colab** (Jupyter Notebook environment).
It requires the following standard Python libraries:
* `numpy`
* `matplotlib`
* `heapq` (built-in)
* `random` (built-in)
* `time` (built-in)

## How to Run
1. Open Google Colab and create a new notebook.
2. Paste the provided Python code into a code cell.
3. (Optional) Adjust the `OBSTACLE_DENSITY` variable at the top of the script (0.15 for Low, 0.30 for Medium, 0.45 for High).
4. Run the cell.

## Output and Measures of Effectiveness (MoE)
Upon execution, the script outputs standard Measures of Effectiveness to the console:
* **Execution Time:** How long the A* algorithm took to find the path (in milliseconds).
* **Nodes Explored:** The total number of grid cells evaluated by the algorithm.
* **Total Distance:** The final length of the optimal path.

Finally, it renders a high-contrast 2D grid visualization using `matplotlib`, displaying open terrain, obstacles, the start/goal nodes, and the final path taken.
