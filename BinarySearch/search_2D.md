[Problem Link](https://leetcode.com/problems/search-a-2d-matrix/submissions/2203003452/?utm_source=chatgpt.com)

```
class Solution {
    public boolean searchMatrix(int[][] arr, int target) {
        int low=0;
        int high=arr.length*arr[0].length-1;
        int n=arr[0].length;
        while(low<=high){
            int mid=low+(high-low)/2;
            int row=mid/n;
            int col=mid%n;
            if(arr[row][col]==target){
                return true;
            }
            else if(arr[row][col]>target){
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return false;
    }
}

```

# Complexity

Time:O(log(m*n))

Space:O(m+n)
