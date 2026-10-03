# Variable starting and ending points

[Problem Link](https://leetcode.com/problems/minimum-falling-path-sum/)

# recurrsion
```
import java.util.*;

public class subarray_sum_k {
    static int min_sum;
    static void find(int arr[][],int row,int col,int score){
        if(row==arr.length-1){
            min_sum=Math.min(min_sum,score+arr[row][col]);
            return;
        }
        if(row+1<arr.length && col-1>=0){
            find(arr,row+1,col-1,score+arr[row][col]);
        }
        if(row+1<arr.length && col>=0 && col<arr[0].length){
            find(arr,row+1,col,score+arr[row][col]);
        }
        if(row+1<arr.length && col+1<arr[0].length){
            find(arr,row+1,col+1,score+arr[row][col]);
        }
    }
    public static void main(String args[]){
//        int arr[][]={{2,1,3},{6,5,4},{7,8,9}};
//        int arr[][]={{-19,57},{-40,-5}};
        int arr[][]={{-80,-13,22},{83,94,-5},{73,-48,61}};
        int min=Integer.MAX_VALUE;
        min_sum=Integer.MAX_VALUE;
        int src[]=new int[2];
        for(int i=0;i<arr[0].length;i++){
            if(min>arr[0][i]){
                min=arr[0][i];
                src[0]=0;
                src[1]=i;
            }
        }
        find(arr,src[0],src[1],0);
        System.out.println(min_sum);
    }
}
```

```
class Solution {
    static int find(int [][]mat,int m,int n,int i,int j){
        if(j<0 || j>=n){
            return Integer.MAX_VALUE;
        } 
          if(i==0) 
          return mat[i][j];
      int up=find(mat,m,n,i-1,j);
      int leftdiag=find(mat,m,n,i-1,j-1);
      int rightdiag=find(mat,m,n,i-1,j+1);
      return Math.min(up,Math.min(leftdiag,rightdiag))+mat[i][j];
    }
    public int minFallingPathSum(int[][] matrix) {
         int m=matrix.length;
         int n=matrix[0].length;
         int ans=Integer.MAX_VALUE;
         for(int j=0;j<n;j++){
          ans=Math.min(find(matrix,m,n,m-1,j),ans);
         }
         return ans;
    }
}
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
    static int find(int [][]mat,int m,int n,int [][]dp){
        for(int j=0;j<n;j++){
            dp[0][j]=mat[0][j];
        }
        for(int i=1;i<m;i++){
            for(int j=0;j<n;j++){
      int up=dp[i-1][j];
      int leftdiag=(j>0)?dp[i-1][j-1]:Integer.MAX_VALUE;
      int rightdiag=(j<m-1)?dp[i-1][j+1]:Integer.MAX_VALUE;
      dp[i][j]=Math.min(up,Math.min(leftdiag,rightdiag))+mat[i][j];
        }
        }
             int ans = Integer.MAX_VALUE;
        for (int j = 0; j < n; j++) {
            ans = Math.min(ans, dp[m-1][j]);
        }
        return ans;

    }
    public int minFallingPathSum(int[][] matrix) {
         int m=matrix.length;
         int n=matrix[0].length;
         int ans=Integer.MAX_VALUE;
         int dp[][]=new int[m][n];
         return find(matrix,m,n,dp);
    }
}
```
# Complexity Analysis

Time:O(m*n)

Space:O(m*n)

# 
