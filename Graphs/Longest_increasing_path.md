# Longest increasing path

[Problem Link](https://www.geeksforgeeks.org/problems/longest-increasing-path-in-a-matrix/1)

# Brute it will give u TLE for last test cases
```
class Solution {
    int maxlen=Integer.MIN_VALUE;
    int rows[]={-1,0,1,0};
    int cols[]={0,1,0,-1};
      void find(int arr[][],int count,int row,int col,int visited[][]){
          visited[row][col]=1;
          maxlen=Math.max(maxlen,count);
          for(int i=0;i<4;i++){
              int newr=row+rows[i];
              int newc=col+cols[i];
              if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]>arr[row][col] && visited[newr][newc]!=1){
                  find(arr,count+1,newr,newc,visited);
              }
          }
          visited[row][col]=0;
      }
    public int longIncPath(int[][] arr, int n, int m) {
        // code here
        int visited[][]=new int[arr.length][arr[0].length];
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                 find(arr,1,i,j,visited);
            }
        }
        return maxlen;
    }
}
```

# Optimised

```
class Solution {
    int rows[]={-1,0,1,0};
    int cols[]={0,1,0,-1};
     int find(int arr[][],int row,int col,int dp[][]){
         if(dp[row][col]!=0){
             return dp[row][col];
         }
         int max=1;
         for(int i=0;i<4;i++){
             int newr=row+rows[i];
             int newc=col+cols[i];
             if(newr>=0 && newr<arr.length && newc>=0 && newc<arr[0].length && arr[newr][newc]>arr[row][col]){
                 max=Math.max(max,1+find(arr,newr,newc,dp));
             }
         }
         dp[row][col]=max;
         return dp[row][col];
     }
    public int longIncPath(int[][] arr, int n, int m) {
        // code here
        int dp[][]=new int[n][m];
        int max=Integer.MIN_VALUE;
        for(int i=0;i<arr.length;i++){
            for(int j=0;j<arr[0].length;j++){
                max=Math.max(find(arr,i,j,dp),max);
            }
        }
        return max;
    }
}
```
