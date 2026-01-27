# Mices and holes

[Problem Link](https://www.geeksforgeeks.org/problems/assign-mice-holes3053/0)

```
class Solution {
    public int assignHole(int[] mices, int[] holes) {
        // code here
        Arrays.sort(mices);
        Arrays.sort(holes);
        int max=Integer.MIN_VALUE;
        for(int i=0;i<mices.length;i++){
            max=Math.max(max,(int)Math.abs(mices[i]-holes[i]));
        }
        return max;
    }
}
```

# Complexity Analysis

Time:O(nlogn)

Space:O(1)
