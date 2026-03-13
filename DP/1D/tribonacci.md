# Tribonacci

[Problem link](https://leetcode.com/problems/n-th-tribonacci-number/submissions/1946709973/)

# Usual method

```
class Solution {
    static int tribo(int n){
        if(n==0){
            return n;
        }
        if(n==1 || n==2){
            return 1;
        }
        return tribo(n-1)+tribo(n-2)+tribo(n-3);
    }
    public int tribonacci(int n) {
        return tribo(n);
    }
}
```

# Memoization

```
class Solution {
    static int tribo(int n,int []dp){
       if(n==0){
        return dp[n]=0;
       }
       if(n==1 || n==2){
        return 1;
       }
      if(dp[n]!=-1){
        return dp[n];
      }
      dp[n]=tribo(n-1,dp)+tribo(n-2,dp)+tribo(n-3,dp);
      return dp[n];
    }
    public int tribonacci(int n) {
        int dp[]=new int[n+1];
        Arrays.fill(dp,-1);
        return tribo(n,dp);
    }
}
```

# Tabulation
```
class Solution {
    static int tribo(int n,int []dp){
        for(int i=3;i<=n;i++){
            dp[i]=dp[i-1]+dp[i-2]+dp[i-3];
        }
        return dp[n];
    }
    public int tribonacci(int n) {
        int dp[]=new int[n+1];
        dp[0]=0;
        if(n>0){
            dp[1]=1;
        }
        if(n>1){
            dp[2]=1;
        }

        return tribo(n,dp);
    }
}
```
# Complexity Analysis

Time:O(3^n)

Space:O(n)
