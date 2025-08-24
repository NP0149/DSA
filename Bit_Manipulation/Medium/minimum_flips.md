# Minimum number of flips to reach goal number

[Problem Link](https://leetcode.com/problems/minimum-bit-flips-to-convert-number/submissions/1747020659/)

# Approach-I

```
class Solution {
    public int minBitFlips(int start, int goal) {
        int m=start^goal;
        int count=0;
         while(m!=0){
            if((m&1)==1){
               count++;
            }
            m=m>>1;
         }
         return count;
    }
}
```

# Complexity Analysis

Time:O(log n)

Space:O(1)
