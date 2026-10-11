# AI Contribution Log — SLE-4

## 1. Project Details

- **Project:** Maze Solving & Profiling System
- **Student:** Prathamesh Shivaji Shingate
- **PRN:** 25UAM091
- **Division:** B
- **Course:** 02AML204 — Introduction to Artificial Intelligence

## 2. AI Tool Used

**Claude (Anthropic)**

AI was used as a supporting tool for documentation, writing improvement, and viva preparation.

## 3. What AI Did

1. Helped structure the Architecture Decision Record into sections such as Context, Decision, Alternatives, Rationale, and Consequences.
2. Helped improve the clarity and grammar of the technical explanations.
3. Helped organize the BFS and DFS experimental results into a comparison table.
4. Helped explain the advantages and limitations of selecting BFS as the default solver.
5. Suggested viva preparation questions related to the architecture decision.
6. Helped organize the AI contribution note and project summary.

## 4. What I Did Myself

1. Ran the BFS and DFS experiments during SLE-2.
2. Collected execution-time measurements and the number of nodes expanded.
3. Used `time.perf_counter` to measure execution time.
4. Used `cProfile` to examine performance during repeated solves.
5. Created and studied the C4 architecture diagrams in SLE-3.
6. Used my experimental measurements and architecture understanding to decide that BFS should be the default solver.
7. Compared the recorded results and checked the reported figures against my previous reports.
8. Reviewed the advantages, limitations, alternatives, and consequences of the architecture decision.
9. Prepared to explain the decision and experimental evidence during the viva.

## 5. Evidence Supporting the Decision

My recorded results for the 25 × 25 maze were:

| Measurement | DFS | BFS |
|---|---:|---:|
| Execution time | 0.9340 ms | 0.2284 ms |
| Nodes expanded | 611 | 213 |

These results supported the selection of BFS as the default solver.

## 6. Declaration

I used Claude (Anthropic) to assist with the structure and wording of my SLE-4 documentation and viva preparation.

The experimental measurements, performance observations, architecture understanding, and final choice of BFS are based on my project work and the results recorded in my SLE-2 and SLE-4 reports.

I reviewed the documentation and take responsibility for explaining the architecture decision and its supporting evidence.

---

