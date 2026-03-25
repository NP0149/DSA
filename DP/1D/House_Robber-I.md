# House Robber -I

[Problem Link](https://leetcode.com/problems/house-robber/submissions/1958561252/)

# Brute Force
```
class Solution {
    static int robbing(int nums[],int val){
        if(val>=nums.ln)ength){
            return 0;
        }
        int take=nums[val]+robbing(nums,val+2);
        int skip=robbing(nums,val+1);
        return Math.max(take,skip);
    }
    public int rob(int[] nums) {
        return robbing(nums,0);
    }
}
```
# Complexity 

Time:O(2^n)

Space:O(n)


# Memoization 

```
class Solution {
    static int robbing(int nums[],int val,int dp[]){
        if(val>=nums.length){
            return 0;
        }
        if(dp[val]!=-1){
            return dp[val];
        }
        int take=nums[val]+robbing(nums,val+2,dp);
        int skip=robbing(nums,val+1,dp);
        dp[val]=Math.max(take,skip);
        return dp[val];
    }
    public int rob(int[] nums) {
        int dp[]=new int[nums.length];
        Arrays.fill(dp,-1);
        return robbing(nums,0,dp);
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)

# Tabulation

```
class Solution {
    public int rob(int[] nums) {
       int dp[]=new int[nums.length];
       if(nums.length>0){
       dp[0]=nums[0];
       }
       if(nums.length>1){
       dp[1]=Math.max(nums[0],nums[1]);
       }
       for(int i=2;i<nums.length;i++){
        int take=nums[i]+dp[i-2];
        int skip=dp[i-1];
        dp[i]=Math.max(take,skip);
       }
       return dp[nums.length-1];
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(n)
