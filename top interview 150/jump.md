# jump

[Problem Link](https://leetcode.com/problems/jump-game/description/?envType=study-plan-v2&envId=top-interview-150)

```
class Solution {
    boolean find(int arr[],int indx){
        if(indx>=arr.length-1){
            return true;
        }
        for(int i=1;i<=arr[indx];i++){
            if(find(arr,indx+i)){
                return true;
            }
        }
        return false;
    }
    public boolean canJump(int[] arr) {
        if(arr.length==1){
            return true;
        }
        if(arr[0]==arr.length-1){
            return true;
        }
        return find(arr,0);
    }
}
```




```
class Solution {
    public boolean canJump(int[] nums) {
        int maxReach = 0; // Maximum index we can reach

        for (int i = 0; i < nums.length; i++) {
            if (i > maxReach) 
            return false; // If current index is not reachable
            maxReach = Math.max(maxReach, i + nums[i]); // Update max reachable index
            if (maxReach >= nums.length - 1) 
            return true; // If we can reach the last index, return true
        }
        return false;
    }
}

```
