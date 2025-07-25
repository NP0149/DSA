# Maximum count of positive and negative elements in array

[Problem Link](https://leetcode.com/problems/maximum-count-of-positive-integer-and-negative-integer/description/)

# Approach-I

1)as 0 neither positive nor negative ,consider target as 0,then find the lower bound and upper bound of 0,and then there you go

```
class Solution {
    public static int rightmost(int arr[],int target){
        int low=0;
        int n=arr.length;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]==target){
                low=mid+1;
            }
            else if(arr[mid]<target){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return low;
    }
    public static int leftmost(int arr[],int target){
        int low=0;
        int n=arr.length;
        int high=n-1;
        while(low<=high){
            int mid=(low+high)/2;
            if(arr[mid]==target){
                high=mid-1;
            }
            else if(arr[mid]<target){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return low;
    }
    public int maximumCount(int[] arr) {
        int n=arr.length;
        int neg=n-rightmost(arr,0);
        int pos=leftmost(arr,0);
        return Math.max(neg,pos);
    }
}
```
# Complexities

Time:O(log n)

Space:O(1)
