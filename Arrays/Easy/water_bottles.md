# Water Bottles

[Problem Link](https://leetcode.com/problems/water-bottles/?envType=daily-question&envId=2025-10-01)


# Approach-I

```
class Solution {
    public int numWaterBottles(int n, int k) {
        int count=n;
        while(n>=k){
         count+=n/k;
         n=(n/k)+(n%k);
       }
       return count;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)
