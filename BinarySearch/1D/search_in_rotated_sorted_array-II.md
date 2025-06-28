# Search in rotated sorted array-II

[Problem Link](https://leetcode.com/problems/search-in-rotated-sorted-array-ii/)

# Approach-I

1)find mid

2)if the elements at low and mid and high are same then low=low+1 and high should be high-1

3)find the sorted sub array find the range in which the target lies in the array ,then eliminate the other half of array

```
class Solution {
    public boolean search(int[] arr, int target) {
        int n=arr.length;
        int low=0;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]==target){
                return true;
            }
            if(arr[low]==arr[mid] && arr[mid]==arr[high]){
                low=low+1;
                high=high-1;
                continue;
            }
            else if(arr[mid]>=arr[low]){
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
        return false;
    }
}
```

# Complexities

Time:O(log N);

Space:O(1)
