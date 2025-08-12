

## Project: graph‑algorithms (C Implementations)

**Source:** (https://github.com/dippedrusk/graph-algorithms)

---

### 1. Overview

This repository provides C implementations of key graph algorithms:

* **Dijkstra’s Algorithm**: Finds shortest paths in graphs with non-negative weights.
* **Prim’s Algorithm**: Constructs a minimum spanning tree (MST) using a greedy approach.
* **Kruskal’s Algorithm**: Builds an MST using Union-Find on sorted edges.
* **Bellman–Ford Algorithm**: Computes shortest paths and supports graphs with negative weights.

All algorithms share a common graph input parsing module.

---

### 2. Project Structure

```
graph-algorithms/
├── graph_input.c
├── graph_input.h
├── dijkstra.c
├── prim.c
├── kruskal.c
├── bellmanford.c
├── Makefile
└── README.md
```

---

### 3. Module & Function Breakdown

#### 3.1 **graph\_input.c / graph\_input.h**

* **Purpose:** Contains functions to read graph data from files and construct internal representations.
* **Key Functions:**

  * `Graph* read_graph(const char* filename);` – Parses input file and returns a populated `Graph`.
  * `void free_graph(Graph* g);` – Frees all memory allocated for the graph.

#### 3.2 **dijkstra.c**

* **Purpose:** Implements Dijkstra’s algorithm with a priority queue.
* **Key Functions:**

  * `void dijkstra(Graph* g, int src);` – Calculates shortest paths from a source vertex.
  * `PQNode extract_min(PriorityQueue* pq);` – Retrieves the vertex with the smallest tentative distance.
  * `void decrease_key(PriorityQueue* pq, int node, int new_dist);` – Updates a vertex’s distance.

#### 3.3 **prim.c**

* **Purpose:** Generates an MST by growing a set of connected vertices.
* **Key Function:**

  * `void prim(Graph* g, int start);` – Selects minimal connecting edges until all vertices are in MST.

#### 3.4 **kruskal.c**

* **Purpose:** Constructs an MST using edge sorting and Union-Find.
* **Key Functions:**

  * `void kruskal(Graph* g);` – Processes sorted edges, joining sets when no cycle is formed.
  * `int find_set(int parent[], int v);` – Finds the root of a set.
  * `void union_sets(int parent[], int rank[], int a, int b);` – Merges two sets.

#### 3.5 **bellmanford.c**

* **Purpose:** Computes shortest paths, supports negative weights.
* **Key Function:**

  * `void bellman_ford(Graph* g, int src);` – Relaxes all edges `V-1` times and checks for negative cycles.

---

### 4. Data Structures

* **Graph:** Likely includes vertex count, edge list or adjacency matrix, and weight storage.
* **Priority Queue:** Used in Dijkstra’s and Prim’s algorithms.
* **Union-Find:** Used in Kruskal’s algorithm.
* **Edge List:** Used in Kruskal’s and Bellman–Ford algorithms.

---

### 5. Build & Execution

```bash
make all             # Build all programs
./dijkstra sample.txt
./prim sample.txt
./kruskal sample.txt
./bellmanford sample.txt
```

Replace `sample.txt` with your graph input file.

---

### 6. Notes

* Input format generally:

```
<num_vertices> <num_edges>
u v weight
u v weight
...
```

* Code is modular – each algorithm is built and run separately.
* `graph_input.c` standardizes graph parsing for all algorithms.

---
