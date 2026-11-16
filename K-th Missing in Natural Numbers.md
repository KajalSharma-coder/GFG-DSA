## 01. K-th Missing in Natural Numbers

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/k-th-missing-element-in-natural-numbers/1)

### Problem Description

**Task:** Given an array arr[] of distinct positive integers and a positive integer k. Consider an infinite sequence of natural numbers starting from 1. The task is to remove all elements present in arr[] from this sequence.Find the k-th smallest number in the remaining sequence.Note: Your solution must run in O(1) auxiliary space.Examples:Input: arr[] = [1, 9, 5, 2], k = 6Output: 10Explanation: After removing [1, 2, 5, 9] from the natural numbers, the remaining sequence is: 3, 4, 6, 7, 8, 10, 11, .... and so on. The 6th number in this sequence is 10, so the answer is 10.Input: arr[] = [1, 2, 3, 4], k = 1Output: 5Explanation: After removing [1, 2, 3, 4] from the natural numbers, the remaining sequence is: 5, 6, 7, .... and so on. The 1st number in the sequence is 5, so the answer is 5.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(n log n)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-16 18:24:36
- **Status:** Correct
- **Marks:** 4

```cpp
class Solution {
public:
    int findKthSmall(vector<int>& arr, int k) {
        int n = arr.size();

        int low = k;
        int high = k + n;

        while (low < high) {
            int mid = low + (high - low) / 2;

            int count = 0;

            for (int x : arr) {
                if (x <= mid) {
                    count++;
                }
            }

            int missing = mid - count;

            if (missing < k) {
                low = mid + 1;
            } 
            else {
                high = mid;
            }
        }

        return low;
    }
};
```

*Generated on: 11/16/2026, 6:25:01 PM*