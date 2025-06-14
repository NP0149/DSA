# Find first and last position in an array

[Problem Link](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/)

```
class Solution {
    public int[] searchRange(int[] arr, int target) {
        //for the first occurance
        int n=arr.length;
        int newarr[]=new int[2];
        int pos=-1;
        newarr[0]=-1;
        newarr[1]=-1;
        for(int i=0;i<n;i++){
            if(arr[i]==target){
                newarr[0]=i;
                newarr[1]=i;
                  pos=i;
                  break;
            }
        }
        for(int i=0;i<n;i++){
            if(arr[i]==target && i!=pos){
                 newarr[1]=i;
            }
        }
        return newarr;
    }
}
```

# Complexities

Time:O(n)

Space:O(1)
