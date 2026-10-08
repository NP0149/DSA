# jump

[Problem Link](https://leetcode.com/problems/jump-game/description/?envType=study-plan-v2&envId=top-interview-150)

# Optimised

```
class Solution {
    public boolean canJump(int[] arr) {
        int currend=0;
        int farend=0;
        for(int i=0;i<arr.length;i++){
         farend=Math.max(farend,i+arr[i]);
         if(i==currend){
            currend=farend;
            if(currend>=arr.length-1){
                return true;
            }
            if(currend==i){
                return false;
            }
         }
        }
        return false;
    }
}
```

# recurrsion

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
# Memoisation
```
class Solution {
    int find(int arr[],int indx,int dp[]){
        if(indx>=arr.length-1){
            return 1;
        }
        if(dp[indx]!=-1){
            return dp[indx];
        }
        for(int i=1;i<=arr[indx];i++){
            if(find(arr,indx+i,dp)==1){
                return dp[indx]=1;
            }
        }
        return dp[indx]=0;
    }
    public boolean canJump(int[] arr) {
        if(arr.length==1){
            return true;
        }
        if(arr[0]==arr.length-1){
            return true;
        }
        int dp[]=new int[arr.length];
        Arrays.fill(dp,-1);
        return find(arr,0,dp)==1;
    }
}
```
# Tabulation

```

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
