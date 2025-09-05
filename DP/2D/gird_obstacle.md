# Grid with Obstacle

[Problem Link](https://leetcode.com/problems/unique-paths-ii/)

# Usual method(Using recurrsion)

```
class Solution {
    static int find(int [][]arr,int m,int n){
        if(m<0 || n<0 || arr[m][n]==1){
            return 0;
        }
            if(m==0 && n==0){
            return 1;
        }
        int right=find(arr,m-1,n);
        int down=find(arr,m,n-1);
        return right+down;
    }
    public int uniquePathsWithObstacles(int[][] obsarr) {
        int m=obsarr.length;
        int n=obsarr[0].length;
        if(m==1 && obsarr[m-1][0]==1){
            return 0;
        }
          if(m==0 && obsarr[m-1][0]==1){
            return 1;
        }
       return find(obsarr,m-1,n-1);
    }
}
```
# Complexities

Time:O(2^(m+n))

Space:O(m+n)


# Memoization

```
class Solution {
    static int find(int [][] mat,int [][]dp,int m,int n){
        if(m<0 || n<0 || mat[m][n]==1){
            return 0;
        }
       if(m==0 && n==0){
        return 1;
       }
       if(dp[m][n]!=-1){
        return dp[m][n];
       }
       int right=find(mat,dp,m-1,n);
       int down=find(mat,dp,m,n-1);
       return dp[m][n]=right+down;
    }
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m=obstacleGrid.length;
        int n=obstacleGrid[0].length;
        int [][]dp=new int[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                dp[i][j]=-1;
            }
        }
        return find(obstacleGrid,dp,m-1,n-1);
    }
}
```

# Comlexities

Time:O(m*n)

Space:O(m*n)

# Tabulation

```
class Solution {
    static int find(int [][] mat,int [][]dp,int m,int n){
      dp[0][0]=mat[0][0]==1 ? 0:1;
      for(int i=1;i<n;i++){
        if(mat[0][i]==1){
             dp[0][i]=0;
        }
        else{
            dp[0][i]=dp[0][i-1];
        }
      }
      for(int j=1;j<m;j++){
        if(mat[j][0]==1){
        dp[j][0]=0;
        }
        else{
            dp[j][0]=dp[j-1][0];
        }
      }
     for(int i=1;i<m;i++){
        for(int j=1;j<n;j++){
            if(mat[i][j]!=1)
            dp[i][j]=dp[i-1][j]+dp[i][j-1];
            else{
                dp[i][j]=0;
            }
        }
     }
     return dp[m-1][n-1];
    }
    public int uniquePathsWithObstacles(int[][] obstacleGrid) {
        int m=obstacleGrid.length;
        int n=obstacleGrid[0].length;
        int [][]dp=new int[m][n];
        return find(obstacleGrid,dp,m,n);
    }
}
```

# Complexities

Time:O(m*n)

Space:O(m*n)


