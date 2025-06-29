# Single Element in an array

[Problem Link](https://leetcode.com/problems/single-element-in-a-sorted-array/submissions/1679854171/)

# Approach-I

1)find the edge cases first and then start at low=1 and high=length-2

2)in left half the numbers repeating are in even and odd fashion so if you find that then eliminate the left half else eliminate the right half

3)then when the elment is not equals to its right and left just return it

```
class Solution {
    public int singleNonDuplicate(int[] arr) {
        int n=arr.length;
        int low=1;
        int high=n-2;
             if(n==1){
            return arr[0];
        }
        if(arr[0]!=arr[1]){
            return arr[0];
        }
        if(arr[n-2]!=arr[n-1]){
            return arr[n-1];
        }
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]!=arr[mid-1] && arr[mid]!=arr[mid+1]){
                return arr[mid];
            }
            if((mid%2==0 && arr[mid]==arr[mid+1]) || (mid%2==1 && arr[mid]==arr[mid-1])){
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
