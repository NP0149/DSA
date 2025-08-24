# Single number

[Problem Link](https://leetcode.com/problems/single-number/)

# Approach(Best)

```
class Solution {
    public int singleNumber(int[] arr) {
        int m=arr[0];
        for(int i=1;i<arr.length;i++){
          m=m^arr[i];
        }
        return m;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
