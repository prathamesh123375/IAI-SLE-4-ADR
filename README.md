# SLE-4: Architecture Decision Record (ADR)
## Maze Solving & Profiling System

### 1. Project Information

- **Student Name:** Prathamesh Shivaji Shingate
- **PRN:** 25UAM091
- **Division:** B
- **Course:** 02AML204 — Introduction to Artificial Intelligence
- **Date:** 08-10-2026
- **GitHub:** https://github.com/prathamesh123375

### 2. Project Overview

This SLE-4 component focuses on making an architecture decision for the Maze Solving & Profiling System developed and studied in SLE-2 and SLE-3.

The system generates a random perfect maze and finds a path from the top-left cell to the bottom-right cell using two uninformed search algorithms:

- Breadth-First Search (BFS)
- Depth-First Search (DFS)

The main objective of SLE-4 is to decide which algorithm should be the default solver based on experimental results, performance, and system architecture.

### 3. Architecture Decision

**Decision: Use queue-based BFS as the default solver and retain stack-based DFS as the baseline.**

BFS uses a queue implemented with `deque`, while DFS uses a list as a stack.

Both algorithms share the same Search Engine components, including:

- `neighbors()` function
- Visited Set
- Node Counter
- Goal Test
- Path Reconstructor

The frontier data structure is the only difference between the two search strategies. This design makes the comparison fair and allows the solver to be changed without modifying the other system components.

### 4. Experimental Results

The decision is supported by my SLE-2 measurements, using five runs per maze size and `time.perf_counter` for timing.

| Maze Size | DFS Time (ms) | BFS Time (ms) | DFS Nodes | BFS Nodes |
|---|---:|---:|---:|---:|
| 5 × 5 | 0.0206 | 0.0121 | 15 | 13 |
| 12 × 12 | 0.1525 | 0.1279 | 129 | 136 |
| 25 × 25 | 0.9340 | 0.2284 | 611 | 213 |

### 5. Result Analysis

- BFS was faster than DFS in all three tested cases.
- In the 25 × 25 maze, BFS was approximately 4.1 times faster.
- BFS expanded 213 nodes, whereas DFS expanded 611 nodes in the 25 × 25 test.
- Both algorithms returned identical path lengths of 11, 65, and 165 for the three respective test cases.
- The `cProfile` results for 200 repeated solves of the 25 × 25 maze showed that `neighbors()` was the most expensive shared helper.

### 6. Alternatives Considered

**DFS as the default:** Rejected because performance depends on the neighbor order and the branches explored before reaching the goal.

**A* Search:** Not implemented in this component. It would require a priority queue and heuristic logic.

**Iterative Deepening DFS and Bidirectional Search:** Considered possible options for larger search spaces, but their additional complexity was not justified for the current 25 × 25 tests.

### 7. Advantages and Limitations

**Advantages of BFS**
- Faster in all three recorded experiments.
- Guarantees a shortest path in an unweighted graph.
- Provides a clear and fair comparison with DFS.
- Can be replaced or extended without changing the whole architecture.

**Limitations**
- BFS can consume substantial memory because it stores frontier nodes.
- The experiment covered only three maze sizes, one fixed neighbor order, and perfect mazes.
- Performance may differ with other maze types and implementations.


### 10. Conclusion

Based on the experimental measurements and the SLE-3 architecture, BFS was selected as the default solver for the Maze Solving & Profiling System. It was faster in all three recorded tests and expanded substantially fewer nodes in the largest test.

The shared Search Engine design also makes it easier to replace or extend the search strategy in the future.

### References

- SLE-2 Profiling Report — 22-09-2026
- SLE-3 C4 Architecture Report — 01-10-2026
- SLE-4 Architecture Decision Record — 08-10-2026
