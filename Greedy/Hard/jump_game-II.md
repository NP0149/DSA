# Jump Game II

[Problem Link](https://leetcode.com/problems/jump-game-ii/)\


```
class Solution {
    public int jump(int[] arr) {
        int l=0;
        int r=0;
        int n=arr.length;
        int jumps=0;
        while(r<n-1){
               int far=0;
            for(int indx=l;indx<=r;indx++){
                far=Math.max(far,arr[indx]+indx);
            }
            l=r+1;
            r=far;
          jumps+=1;
        }
        return jumps;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
