# Rotate 2D array 90 degrees

[Problem Link](https://leetcode.com/problems/rotate-image/)

# Approach-I

1)transpose the matrix and then reverse each array elements

```
class Solution {
    //to reverse each row
    public static void rev(int arr[][],int low,int high,int row){
        int i=low;
        int j=high;
        while(i<j){
            int temp=arr[row][i];
            arr[row][i]=arr[row][j];
            arr[row][j]=temp;
            i++;
            j--;
        }
    }
    //to transpose the matrix
    public static void trans(int m[][]){
        int n=m.length;
        for(int i=0;i<n;i++){
        for(int j=0;j<i;j++){
                int temp=m[i][j];
                m[i][j]=m[j][i];
                m[j][i]=temp;
            }
        }
        for(int i=0;i<n;i++){
            rev(m,0,n-1,i);
        }
    }
    //to rotate the matrix
    public void rotate(int[][] m) {
        trans(m);
    }
}
```
# Complexities

Time:O(n^2);

Space:O(1);//inplace array elements
