# Count number of ways to reach nth stair by standing at the first stair

[Problem Link](https://leetcode.com/problems/climbing-stairs/)

# Approach-I

1)exactly fibonacci only but we need to find the fibonacci for n+1 

```
class Solution {
   static int find(int n){
    if(n==0 || n==1) return n;
    int curr=0;
    int prev1=1;
    int prev2=0;
    for(int i=2;i<=n;i++){
  curr=prev1+prev2;
  prev2=prev1;
  prev1=curr;
    }
    return prev1;
   }
    public int climbStairs(int n) {
      return find(n+1);
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)

# Using tabulation

```
class Solution {
     static int mincost(int []cost,int idx,int dp[]){
          dp[0]=cost[0];
        if(idx>0){
        dp[1]=cost[1];
        }
        for(int i=2;i<idx;i++){
            dp[i]=cost[i]+Math.min(dp[i-1],dp[i-2]);
        }
        return Math.min(dp[idx-1],dp[idx-2]);
    } 
    public int minCostClimbingStairs(int[] cost) {
        int idx=cost.length;
        int dp[]=new int[cost.length];
        Arrays.fill(dp,-1);
        return mincost(cost,idx,dp);
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)

# Using memoization
```
class Solution {
    static int find(int cost[],int n,int dp[]){
        if(n==0 || n==1){
            return dp[n]=cost[n];
        }
        if(dp[n]!=-1){
            return dp[n];
        }
        return dp[n]=cost[n]+Math.min(find(cost,n-1,dp),find(cost,n-2,dp));
    }
    public int minCostClimbingStairs(int[] cost) {
        int dp[]=new int[cost.length];
        int n=cost.length;
        Arrays.fill(dp,-1);
        return Math.min(find(cost,n-1,dp),find(cost,n-2,dp));
    }
}
```

# Compelxity Analysis

Time:O(n)

Space:O(n)

