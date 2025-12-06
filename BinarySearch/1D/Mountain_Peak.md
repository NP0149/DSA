# Mountain Peak

[Problem Link](https://leetcode.com/problems/find-peak-element/submissions/1680408471/)

# Approach-I

1)just find mid write all edge cases,start low from 1 and high from length-1

2)arr[mid]>arr[mid-1] just eliminate the left half and then eliminate the right half

3)if arr[mid-1]<arr[mid] and arr[mid]>arr[mid+1] then return mid

```
class Solution {
    public int findPeakElement(int[] arr) {
        int n=arr.length;
        int low=1;
        int high=n-2;
        if(n==1){
            return 0;
        }
        if(arr[0]>arr[1]){
            return 0;
        }
        if(arr[n-1]>arr[n-2]){
            return n-1;
        }
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]>arr[mid-1] && arr[mid]>arr[mid+1]){
                return mid;
            }
            if(arr[mid]>=arr[mid-1]){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return -1;
    }
}
```
# Complexities

Time:O(log N)

Space:O(1)
