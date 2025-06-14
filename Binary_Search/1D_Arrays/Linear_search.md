# Linear Search

[Problem Link](https://leetcode.com/problems/binary-search/description/)

```
class Solution {
    public static int bs(int arr[],int target,int low,int high){
        if(low>high){
        return -1;
        }
        int mid=(low+high)/2;
        if(arr[mid]==target){
            return mid;
        }
        else if(arr[mid]>target){
            return bs(arr,target,low,mid-1);
        }
        else{
            return bs(arr,target,mid+1,high);
        }
    }
    public int search(int[] arr, int target) {
       int n=bs(arr,target,0,arr.length-1);
       return n;
}
}
```

## Complexities

Time:O(logn)

Space:O(1)
