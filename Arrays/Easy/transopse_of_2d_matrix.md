# Transpose of a matrix
[problem link](https://leetcode.com/problems/transpose-matrix/)

1)In a transpose of a matrix number of rows become columns and number of columns become rows
and considering a new matrix named transpose and then assinging the previous matrix values to it by reversing the rows and columns

```Java
class Solution {
    public int[][] transpose(int[][] matrix) {
        int n=matrix.length;
        int m=matrix[0].length;
        int transpose[][]=new int[m][n];
        for(int i=0;i<m;i++)
        {  for(int j=0;j<n;j++){
             transpose[i][j]=matrix[j][i];
             }
        }
        return transpose;
    }
}
```
# complexities
time coplexity:O(N)
