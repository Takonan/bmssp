# BMSSP vs Dijkstra's Algorithm Visualization

This project is an interactive, visual comparison of two algorithms for the Single-Source Shortest Path (SSSP) problem: the classic Dijkstra's Algorithm and a more recent pivot-based method, the Bounded Multi-Source Shortest Path (BMSSP) algorithm.

It allows users to see how each algorithm explores a graph to find the shortest path from a single starting node to all other nodes.

## The Algorithms

### 1. Dijkstra's Algorithm

Dijkstra's is one of the most famous graph algorithms. It works by maintaining a priority queue of nodes to visit, always choosing the unvisited node with the smallest known distance from the start. While effective, its performance can be limited by the need to sort this priority queue in every step, creating a "sorting barrier."

### 2. Bounded Multi-Source Shortest Path (BMSSP)

BMSSP is a more modern approach designed to overcome Dijkstra's sorting barrier. Instead of relaxing one node at a time, it works in rounds:

* **Find Pivots:** It first explores a short distance from the current frontier to identify a set of "pivot" nodes.
* **Process Subproblems:** It then solves smaller, independent SSSP problems starting from these pivots.
* **Update:** Finally, it updates the main distance values and begins a new round.

By processing nodes in batches, it can be more efficient on certain types of graphs.

## How to Use the Visualization

The interface provides several controls to explore how the algorithms perform on different graph structures.

* **Graph:** Use the dropdown menu to select from several procedurally generated graph types:
    * `Bottleneck`: A graph where most nodes are connected through a single central point.
    * `Grid`: A standard, uniform grid layout.
    * `Barbell`: Two dense clusters of nodes connected by a single edge.
    * `Caveman`: Several dense clusters (caves) that are sparsely connected to each other.
    * `Hub & Spoke`: A central hub node connected to many outer "spoke" nodes.
* **Speed:** Use the slider to control the animation speed of the algorithms.
* **Start / Pause / Restart:** This button controls the animation. Press it once to start, again to pause, and once more to resume. When the algorithms are finished, it will change to "Restart."

## Legend

The nodes in the graph are color-coded to represent their current state in the algorithm's execution:

* <span style="color:#84CC16;">**Green (Lime)**</span>: **Completed** - The shortest path to this node has been found and finalized.
* <span style="color:#F97316;">**Orange**</span>: **Frontier/Queue** - The node is in the main priority queue to be visited.
* <span style="color:#3B82F6;">**Blue**</span>: **Pivot** - (BMSSP only) A node selected as a pivot for the current round.
* <span style="color:#A855F7;">**Purple**</span>: **Touched (W)** - (BMSSP only) A node that has been reached and had its distance updated.
* <span style="color:#EC4899;">**Pink**</span>: **Sub-frontier (Si)** - (BMSSP only) A node that is part of the current subproblem being processed.

## Reference

The BMSSP algorithm visualized here is based on the following paper:

Duan, R., Mao, J., Mao, X., Shu, X., & Yin, L. (2025). *Breaking the Sorting Barrier for Directed Single-Source Shortest Paths*. arXiv preprint arXiv:2504.17033. [https://arxiv.org/html/2504.17033v2](https://arxiv.org/html/2504.17033v2)
