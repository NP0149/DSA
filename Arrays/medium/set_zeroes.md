# Mark zeroes in a matrix

[Problem Link](https://leetcode.com/problems/set-matrix-zeroes/submissions/1655248053/)

# Approach-I(Brute Force)

```
class Solution {
    public static void change(int arr[][],int p,int q){
        int n=arr.length;
        int t=arr[0].length;
        for(int i=0;i<n;i++){
            for(int j=0;j<t;j++){
                if((i==p||j==q) && arr[i][j]!=0){
                    arr[i][j]=-999999;
                }
            }
        }
        }
    public void setZeroes(int[][] matrix) {
        int n=matrix.length;
        int m=matrix[0].length;
        int p=-1;
        int q=-1;
      for(int i=0;i<n;i++)  {
        for(int j=0;j<m;j++){
            if(matrix[i][j]==0){
                 change(matrix,i,j);
            }
        }
      }
       for(int i=0;i<n;i++)  {
        for(int j=0;j<m;j++){
            if(matrix[i][j]==-999999){
                matrix[i][j]=0;
            }
        }
    }
    }
}
```
# Complexties

Time:O(n^3)

Space:O(1)
