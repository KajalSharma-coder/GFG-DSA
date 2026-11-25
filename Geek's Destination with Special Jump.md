## 01. Geek's Destination with Special Jump

The problem can be found at the following link: [Question Link](https://www.geeksforgeeks.org/problems/geek-and-her-destination--145724/1)

### Problem Description

**Task:** Geek starts at position 0 on the positive X-axis and needs to reach or pass position d on the positive X-axis. Geek normally follows a repeating movement pattern:Move forward by a units, taking a seconds.Move backward by b units, taking b seconds.Geek also has a special jump that moves him exactly j units forward in 1 second. He can use it at any time, even in the middle of a forward or backward movement, and the journey ends immediately after the jump.Given five integers a, b, d, l, and r. For every integer j in the range [l, r], find the minimum time required for Geek to reach or pass position d. He may either use the special jump or reach the destination using normal movement alone, whichever takes less time.Return the sum of the minimum times for all jump lengths from l to r. Since, the answer can be large, return modulo 10⁹ + 7. Note: Each jump length is considered independently.Examples:Input: a = 2, b = 1, d = 5, l = 3, r = 4Output: 5Explanation: For j = 3, Geek moves 2 units forward, then takes a jump of 3 units to reach the destination. The minimum time required is 3 seconds.For j = 4, Geek moves 1 unit forward, then takes a jump of 4 units to reach the destination. The minimum time required is 2 seconds.Total sum for the range [l, r] = 3 + 2 = 5.Input: a = 4, b = 2, d = 8, l = 2, r = 4Output: 26Explanation:For j = 2, Geek moves 4 units forward, then 2 units backward. She then moves 4 units forward again and takes a jump of 2 units to reach the destination. The minimum time required is 11 seconds.For j = 3, Geek moves 4 units forward, then 2 units backward. She then moves 3 units forward and takes a jump of 3 units to reach the destination. The minimum time required is 10 seconds.For j = 4, Geek moves 4 units forward, then takes a jump of 4 units to reach the destination. The minimum time required is 5 seconds.Total sum for the range [l, r] = 11 + 10 + 5 = 26.

### Time and Auxiliary Space Complexity

- **Expected Time Complexity:** O(1)
- **Expected Auxiliary Space Complexity:** O(1)

### Accepted Solutions (1)

#### Solution 1 (C++)

- **Submitted:** 2026-11-25 23:25:23
- **Status:** Correct
- **Marks:** 8

```cpp
class Solution {
public:
    long long minTime(int a, int b, int d, int l, int r) {
        const long long MOD = 1e9 + 7;

        long long net = a - b;
        long long cycle = a + b;

        auto reach = [&](long long x) -> long long {
            if (x <= a) return x;
            return x + 2LL * b * ((x - a + net - 1) / net);
        };

        long long normal = reach(d);

        auto maxPos = [&](long long t) -> long long {
            long long q = t / cycle;
            long long rem = t % cycle;

            long long cur = q * net + min((long long)a, rem);
            long long prev = (q > 0) ? (q - 1) * net + a : 0;

            return max(cur, prev);
        };

        long long limit = maxPos(normal - 2);

        auto prefix = [&](long long n) -> long long {
            if (n <= 0) return 0;

            long long q = n / net;
            long long rem = n % net;

            return net * q * (q + 1) / 2 + rem * (q + 1);
        };

        long long L = d - r;
        long long R = d - l;

        long long end = min(R, limit);
        long long ans = 0;

        if (L <= end) {
            long long cnt = end - L + 1;
            long long sumH = (L + end) * cnt / 2;

            long long x = max(L, (long long)a + 1);

            if (x <= end) {
                sumH += 2LL * b *
                    (prefix(end - a) - prefix(x - a - 1));
            }

            ans = (sumH + cnt) % MOD;
        }

        long long start = max(L, end + 1);

        if (start <= R) {
            long long cnt = R - start + 1;
            ans = (ans + cnt * (normal % MOD)) % MOD;
        }

        return ans;
    }
};
```

*Generated on: 11/25/2026, 11:26:43 PM*