# Shortest path from 1 to n

[Problem Link](https://www.geeksforgeeks.org/problems/shortest-path-from-1-to-n0156/1)


```
class Solution {
    int find(int n,int indx,int dp[]){
        if(indx==n){
            return 0;
        }
          if(indx>n){
            return (int)1e9;
        }
        if(dp[indx]!=-1){
            return dp[indx];
            }
        int one=1+find(n,indx+1,dp);
        int thrice=1+find(n,indx*3,dp);
        return dp[indx]=Math.min(one,thrice);
    }
    public int minimumStep(int n) {
        // code here
       int dp[]=new int[n];
       Arrays.fill(dp,-1);
        return find(n,1,dp);
    }
}

```
