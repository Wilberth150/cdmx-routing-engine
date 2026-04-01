# cdmx-routing-engine

## 📌 Overview
Shortest path routing engine for the Mexico City Metro system. It models stations and connections as a weighted graph to determine the most time-efficient route between two points, automatically computing the required line transfers.

## ⚙️ Architecture & Algorithms
* **Data Structure:** Graph representation using an **Adjacency Matrix** (`std::vector<std::vector<ConexionFW>>`). This structure was intentionally chosen over an adjacency list to optimize the execution of the base algorithm for a highly-queried network.
* **Core Algorithm:** Implementation of the **Floyd-Warshall Algorithm** for the All-Pairs Shortest Path problem.
* **Computational Complexity:**
  * Pre-computation (Kernel Initialization): O(V^3)
  * User Queries: O(1)
* **Path Reconstruction:** Uses an auxiliary predecessor matrix (`ruta_siguiente`) to store node traces and output the exact path, station by station.
* **Transfer Logic:** The algorithm evaluates edge metadata (subway line names) during path reconstruction to dynamically alert the user about necessary line transfers.

## 🚀 Compilation & Execution
This project is written in pure C++ with no external dependencies, strictly relying on the Standard Template Library (STL) for memory management and dynamic data structures.

To compile using GCC/MinGW from the terminal:

```bash
g++ main.cpp -o cdmx-routing
./cdmx-routing
