# Smallest Divisor

[Problem Link](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/)

```
class Solution {
    public static int fun(int[] arr, int mid) {
        double total = 0;
        for (int i = 0; i < arr.length; i++) {
            total += Math.ceil((double) arr[i] / mid);
        }
        return (int) total;
    }

    public int smallestDivisor(int[] arr, int threshold) {
        int low = 1;
        int high = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++) {
            high = Math.max(high, arr[i]);
        }

        int ans = -1;
        while (low <= high) {
            int mid = (low + high) / 2;
            int find = fun(arr, mid);

            if (find <= threshold) {
                ans = mid;
                high = mid - 1;
            } else {
                low = mid + 1;
            }
        }
        return ans;
    }
}
```

# Complexities

Time:O(n*log(max(array)))

Space:O(1)
