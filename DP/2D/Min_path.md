# Minimum path to take

[Problem Link](https://leetcode.com/problems/minimum-path-sum/)

```
class Solution {
    static int min;
    void find(int arr[][],int row,int col,int score){
    if(row==arr.length-1 && col==arr[0].length-1){
        min=Math.min(min,score);
        return;
    }
    if(row+1>=0 && row+1<arr.length){
        find(arr,row+1,col,score+arr[row+1][col]);
    }
    if(col+1>=0 && col+1<arr[0].length){
        find(arr,row,col+1,score+arr[row][col+1]);
    }
    }
    public int minPathSum(int[][] arr) {
        min=Integer.MAX_VALUE;
        find(arr,0,0,arr[0][0]);
        return min;
    }
}
```

# Tabulation

```
class Solution {
    public int minPathSum(int[][] grid) {
        int m=grid.length;
        int n=grid[0].length;
        int dp[][]=new int[m][n];
        dp[0][0]=grid[0][0];
        for(int i=1;i<m;i++){
            dp[i][0]=dp[i-1][0]+grid[i][0];
        }
        for(int j=1;j<n;j++){
            dp[0][j]=dp[0][j-1]+grid[0][j];
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j]=Math.min(dp[i-1][j],dp[i][j-1])+grid[i][j];
            }
        }
        return dp[m-1][n-1];
    }
}
```
```
class Solution {
    static int min;
    int find(int arr[][],int row,int col,int score,int dp[][]){
    if(row==arr.length-1 && col==arr[0].length-1){
        min=Math.min(min,score);
        dp[row][col]=min;
        return 0;
    }
    if(dp[row][col]!=-1){
        return dp[row][col];
    }
    if(row+1>=0 && row+1<arr.length){
        find(arr,row+1,col,score+arr[row+1][col],dp);
    }
    if(col+1>=0 && col+1<arr[0].length){
        find(arr,row,col+1,score+arr[row][col+1],dp);
    }
    return dp[row][col];
    }
    public int minPathSum(int[][] arr) {
        min=Integer.MAX_VALUE;
        int dp[][]=new int[arr.length][arr[0].length];
        for(int i=0;i<arr.length;i++){
        Arrays.fill(dp[i],-1);
        }
        find(arr,0,0,arr[0][0],dp);
        return dp[arr.length-1][arr[0].length-1];
    }
}
```
# Complexities

Time:O(m*n)

Space:O(m*n)
