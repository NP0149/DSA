# Candies distribution

[Problem Link](https://leetcode.com/problems/distribute-candies-among-children-ii/)


# Approach-I

```
class Solution {
    public long distributeCandies(int n, int limit) {
        long count=0;
        for(int i=0;i<=Math.min(n,limit);i++){
            for(int j=0;j<=Math.min(n-i,limit);j++){
                int z=n-i-j;
                if(z>=0 && z<=limit){
                    count++;
                }
            }
        }
        return count;
    }
}
```

# Complexities

Time:O(n^2);

Space:O(1);

