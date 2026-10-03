# Variable starting and ending points

[Problem Link](https://leetcode.com/problems/minimum-falling-path-sum/)

# Recurrsion

```
```


# Tabulation
```
class Solution {
   
    public int minFallingPathSum(int[][] arr) {
    int dp[][]=new int[arr.length][arr[0].length];
    for(int i=0;i<arr[0].length;i++){
        dp[0][i]=arr[0][i];
    }
    for(int i=1;i<arr.length;i++){
        for(int j=0;j<arr[0].length;j++){
         int left=Integer.MAX_VALUE;
         if(j-1>=0){
            left=dp[i-1][j-1];
         }
         int up=dp[i-1][j];
         int right=Integer.MAX_VALUE;
         if(j+1<=arr[0].length-1){
            right=dp[i-1][j+1];
         }
         dp[i][j]=Math.min(left,Math.min(right,up))+arr[i][j];
        }
    }
    int min=Integer.MAX_VALUE;
    for(int i=0;i<arr[0].length;i++){
        min=Math.min(min,dp[arr.length-1][i]);
    }
    return min;
    }
}
```
