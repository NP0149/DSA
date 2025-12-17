# Jump game

[Problem Link](https://leetcode.com/problems/jump-game/submissions/1858273080/)

```
class Solution {
    public boolean canJump(int[] arr) {
        int max=arr[0];
        for(int i=1;i<arr.length;i++){
            if(max>=i){
                max=Math.max(max,arr[i]+i);
            }
            else{
                return false;
            }
        }
        return true;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
