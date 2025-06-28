# Minimum in an array using logn time complexity

[Problem Link](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/submissions/1679355623/)

# Approach-I

1)if right array is sorted consider min element and eliminate that subarray consider left sub array and then find min and vic versa

2) return minimum

```
class Solution {
    public int findMin(int[] arr) {
        int n=arr.length;
        int low=0;
        int high=n-1;
        int mini=Integer.MAX_VALUE;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[low]<=arr[high]){
              mini=Math.min(mini,arr[low]);
              break; 
            }
            if(arr[low]<=arr[mid]){
                mini=Math.min(mini,arr[low]);
                low=mid+1;
            }
            else{
                mini=Math.min(mini,arr[mid]);
                high=mid-1;
            }
        }
        return mini;
}
}
```

# Complexities

Time:O(log N)

Space:O(1)
