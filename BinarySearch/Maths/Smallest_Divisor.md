# Smallest Divisor 

[Problem Link](https://leetcode.com/problems/find-the-smallest-divisor-given-a-threshold/description/)

# Approach-I

1)we will be given a threshold when we divide all the array elements with a number then by considering ceil value of the divison sum of all the array elements division

2)we need to consider the smallest value so mive high to mid-1 when ceil division value less than else low=mid+1;

3)return low value

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

Time:O(log N)

Space:O(1)
