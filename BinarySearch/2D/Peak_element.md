# Peak element in a 2d matrix

[Problem Link](https://leetcode.com/problems/find-a-peak-element-ii/submissions/1700792047/)

# Approach-I

1)first we need to find the max element in a column if that particular ele is graeter than left and right elements ina row then it is peak element

2)If not apply binary search

```
class Solution {
    public static int find(int [][]mat,int col){
        int n=mat[0].length;
        int m=mat.length;
        int max=Integer.MIN_VALUE;
        int index=-1;
        for(int i=0;i<m;i++){
            if(max<mat[i][col]){
                max=mat[i][col];
                index=i;
            }
        }
        return index;

    }
    public int[] findPeakGrid(int[][] mat) {
        int n=mat.length;
        int m=mat[0].length;
        int low=0;
        int high=m-1;
        int arr[]=new int[2];
        arr[0]=-1;
        arr[1]=-1;
        while(low<=high){
            int mid=(low+high)/2;
            int row=find(mat,mid);
            int left = (mid - 1 >= 0) ? mat[row][mid - 1] : Integer.MIN_VALUE;
            int right = (mid + 1 < m) ? mat[row][mid + 1] : Integer.MIN_VALUE;
            if(mat[row][mid]>left && mat[row][mid]>right){
                arr[0]=row;
                arr[1]=mid;
                return arr;
            }
            else if(mat[row][mid]<left){
                high=mid-1;
            }
            else{
                low=mid+1;
            }

        }
        return arr;
    }
}
```
# Complexity

Time:O(m * logn)

Space:O(1)//though we used the extra array to store row and column to return it ,the array is of fixed length it is not growing with the size so we can consider it as constant space complexitiy
