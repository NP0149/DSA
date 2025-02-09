# ROTATE ARRAY 90 DEGREES

[PROBLEM LINK](https://leetcode.com/problems/rotate-image/description/)

# Approach I

1)transpose the given array
2)then traverse every row and then reverse the array

```Java
class Solution {
    public void rotate(int[][] arr) {
        int n=arr.length;
        int m=arr[0].length;
       for(int i=0;i<m;i++){
          for(int j=0;j<=i;j++){
        int temp=arr[i][j];
        arr[i][j]=arr[j][i];
        arr[j][i]=temp;
          }     
          }
        for(int i=0;i<n;i++){
            int j=0;
            int k=n-1;
            while(j<k){
                int temp=arr[i][j];
                arr[i][j]=arr[i][k];
                arr[i][k]=temp;
                j++;
                k--;
            }
        }
    }
   
}
```
# complexities
time complexity:O(N)
space complexity:O(1)
