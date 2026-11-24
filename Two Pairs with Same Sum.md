## 01. Two Pairs with Same Sum

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/satisfy-the-equation5847/1)

### Problem Description

**Task:** Given an array arr[] of positive integers, find four indices a, b, c, and d such that arr[a] + arr[b] = arr[c] + arr[d], where a, b, c, d are all distinct indices.If multiple such quadruplets exist, return the one that is lexicographically smallest when the indices are considered in the order a, b, c, d. If no such quadruplet exists, return {-1, -1, -1, -1}. Ensure a < b and c < d, and the pair (a, b) is lexicographically smaller than the pair (c, d).Examples:Input: arr[] = [3, 4, 7, 1, 2, 9, 8]

#### Examples

##### Example 1

- **Output:**
```text
[-1, -1, -1, -1]
```
- **Explanation:** No two distinct pairs of indices produce the same sum.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n^2)
- **Expected Auxiliary Space Complexity:** O(n^2)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-24 07:18:10
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    vector<int> findPairs(vector<int>& arr) {
        int n = arr.size();

        unordered_map<long long, vector<pair<int,int>>> mp;

        // Store all pairs according to their sum
        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                long long sum = (long long)arr[i] + arr[j];
                mp[sum].push_back({i, j});
            }
        }

        // Find lexicographically smallest valid quadruplet
        for (int a = 0; a < n; a++) {
            for (int b = a + 1; b < n; b++) {

                long long sum = (long long)arr[a] + arr[b];

                auto &v = mp[sum];

                for (auto &[c, d] : v) {

                    if (make_pair(c, d) <= make_pair(a, b))
                        continue;

                    if (a != c && a != d &&
                        b != c && b != d) {
                        return {a, b, c, d};
                    }
                }
            }
        }

        return {-1, -1, -1, -1};
    }
};
```

*Generated on: 11/24/2026, 7:18:45 AM*