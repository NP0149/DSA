# Search In a Rotated sorted array-I

[Problem Link](https://leetcode.com/problems/search-in-rotated-sorted-array/submissions/1678929566/)

# Approach-I

1)find mid

2)find the sorted sub array

3)eliminate one half of the sub array and then find the value

```
class Solution {
    public int search(int[] arr, int target) {
        int n=arr.length;
        int low=0;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]==target){
                return mid;
            }
            if(arr[low]<=arr[mid]){
                if(arr[low]<=target && target<=arr[mid]){
                    high=mid-1;
                }
                else{
                    low=mid+1;
                }
            }
            else{
                if(arr[mid]<=target && target<=arr[high]){
                    low=mid+1;
                }
                else{
                    high=mid-1;
                }
            }
        }
        return -1;
    }
}
```

# Complexities

Time:O(log N)

Space:O(1)
