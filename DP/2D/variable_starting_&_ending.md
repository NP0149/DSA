# Variable starting and ending points

[Problem Link](https://leetcode.com/problems/minimum-falling-path-sum/)

# recurrsion

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
