# Variable starting and ending points

[Problem Link](https://leetcode.com/problems/minimum-falling-path-sum/)

# recurrsion

```

```

# Complexity Analysis

Time:O(n * 3^m)

Space:O(m)

# memoization

```
class Solution {
    static int find(int [][]mat,int m,int n,int i,int j,int [][]dp){
        if(j<0 || j>=n){
            return Integer.MAX_VALUE;
        } 
          if(i==0) 
          return dp[i][j]=mat[i][j];
      int up=find(mat,m,n,i-1,j,dp);
      int leftdiag=find(mat,m,n,i-1,j-1,dp);
      int rightdiag=find(mat,m,n,i-1,j+1,dp);
      return dp[i][j]=Math.min(up,Math.min(leftdiag,rightdiag))+mat[i][j];
    }
    public int minFallingPathSum(int[][] matrix) {
         int m=matrix.length;
         int n=matrix[0].length;
         int ans=Integer.MAX_VALUE;
         int dp[][]=new int[m][n];
         for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                dp[i][j]=-1;
            }
         }
         for(int j=0;j<n;j++){
          ans=Math.min(find(matrix,m,n,m-1,j,dp),ans);
         }
         return ans;
    }
}
```

# Complexity Analysis

Time:O(n^2)

Space:O(n^2)


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
# Complexity Analysis

Time:O(m*n)

Space:O(m*n)

# 
