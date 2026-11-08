[Problem Link](https://takeuforward.org/practice/dsa/grid-unique-paths)


```
class Solution {
    int find(int m,int n,int row,int col,int dp[][]){
        if(row>=m || col>=n || row<0 || col<0){
            return 0;
        }
        if(row==m-1 && col==n-1){
            return 1;
        }
        if(dp[row][col]!=-1){
            return dp[row][col];
        }
        int right=find(m,n,row,col+1,dp);
        int down=find(m,n,row+1,col,dp);
        return dp[row][col]=right+down;
    }
    public int uniquePaths(int m, int n) {
        int dp[][]=new int[m][n];
        for(int a[]:dp){
            Arrays.fill(a,-1);
        }
    return find(m,n,0,0,dp);
    }
}
```
