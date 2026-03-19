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



# UGV Dynamic Environment Navigation (Continuous Replanning)

## Overview
This project is an advanced simulation of an Unmanned Ground Vehicle (UGV) navigating a 70x70 km battlefield where obstacles are **dynamic and not known a-priori**. 

Unlike standard static pathfinding, the UGV starts with a blank internal map. It utilizes a simulated sensor (with a predefined range) to discover the true environment as it moves. The script implements **Continuous A* Replanning**: the UGV plans a route, takes a step, and scans its surroundings. If a newly discovered obstacle blocks its planned route, it pauses, updates its internal map, and recalculates a new optimal path from its current location.

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
3. (Optional) Adjust the `SENSOR_RANGE` variable at the top of the script to change how far the UGV can "see" in the grid.
4. Run the cell.

## Output and Measures of Effectiveness (MoE)
Upon execution, the script tracks the dynamic performance and outputs the following MoE to the console:
* **Total Execution Time:** The combined time of all planning, moving, and recalculation phases.
* **Total Replans Issued:** How many times the UGV had to recalculate its path due to unexpected obstacles.
* **Actual Distance:** The total number of physical steps the UGV had to take to reach the goal.

The script concludes by rendering a 2D visualization using `matplotlib`. This map uniquely highlights the UGV's final state of knowledge, distinguishing between **Discovered Obstacles** (which the UGV saw and avoided) and **Undiscovered Obstacles** (which existed in the world but were never close enough to the UGV to be detected).
