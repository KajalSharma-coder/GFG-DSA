## 01. Count Edges in Graph

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/count-number-of-edges-in-an-undirected-graph/1)

### Problem Description

**Task:** Given an undirected graph with V vertices numbered from 0 to V - 1, represented by an adjacency list adj[][], where adj[i] contains the vertices adjacent to vertex i. Return the total number of edges present in the graph.Examples:Input: adj[][] = [[1, 2], [0, 2], [0, 1, 3], [2]]Output: 4

#### Examples

##### Example 1

- **Explanation:** The edges in the graph are: (0-1), (0-2), (2-3), (1-2). Hence, total number of edges = 4.Input: adj[][] = [[1], [0, 2], [1, 3], [2]]Output: 3Explanation: The edges in the graph are: (0-1), (1-2), (2-3). Hence, total number of edges = 3.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(V + E)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-27 07:29:54
- **Status:** Correct
- **Marks:** 2

```cpp
class Solution {
public:
    int countEdges(vector<vector<int>> &adj) {
        int edges = 0;

        for (auto &v : adj) {
            edges += v.size();
        }

        return edges / 2;
    }
};
```

*Generated on: 11/27/2026, 7:30:52 AM*