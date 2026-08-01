# Toeplitz matrix

[problem link](https://leetcode.com/problems/toeplitz-matrix/submissions/2090290878/)

```
class Solution {
    static boolean find(int matrix[][],int m,int n){
        int num=matrix[m][n];
        for(int i=m;i<matrix.length;i++){
            if(i<matrix.length && n<matrix[0].length){
                if(matrix[i][n++]!=num){
                    return false;
                }
            }
        }
        return true;
    }
    public boolean isToeplitzMatrix(int[][] matrix) {
        for(int i=0;i<matrix.length;i++){
            for(int j=0;j<matrix[0].length;j++){
                if(find(matrix,i,j)!=true){
                    return false;
                }
            }
        }
        return true;
    }
}
```
