# Search in a 2D matrix

[Problem Link](https://leetcode.com/problems/search-a-2d-matrix/submissions/1699115060/)

# Approach-I(Better)

1)As the elements in the matrix are sorted so we can use binary search,by pasing evry row to the function and by reducing number of operations
so that it will become efficient

```
class Solution {
    public static int find(int []arr,int target){
        int m=arr.length;
        int low=0;
        int high=m-1;
        if(arr[m-1]<target){
            return -1;
        }
        while(low<=high){
            int mid=(low+high)/2;
            if(target==arr[mid]){
                 return 1;
            }
            else if(target>arr[mid]){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return -1;
    }
    public boolean searchMatrix(int[][] mat, int target) {
        int ans=-1;
        for(int i=0;i<mat.length;i++){
            int k=find(mat[i],target);
             if(k==-1){
                continue;
             }
             else{
                ans=find(mat[i],target);
                if(ans==1){
                    return true;
                }
             }
        }
        return false;
    }
}
```
# Complexities

Time:O(n*log m)

Space:O(1)
