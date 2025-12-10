# Trapping rain water

[Problem Link](https://leetcode.com/problems/trapping-rain-water/submissions/1852087460/)

```
class Solution {
    public int trap(int[] arr) {
        int prefixmax[]=new int[arr.length];
        int suffixmax[]=new int[arr.length];
        int n=arr.length;
        prefixmax[0]=arr[0];
        for(int i=1;i<n;i++){
            prefixmax[i]=Math.max(prefixmax[i-1],arr[i]);
        }
        suffixmax[n-1]=arr[n-1];
        for(int i=n-2;i>=0;i--){
            suffixmax[i]=Math.max(suffixmax[i+1],arr[i]);
        }
        int t=0;
        int total=0;
        while(t<n){
            int leftmax=prefixmax[t];
            int rightmax=suffixmax[t];
            total+=Math.min(leftmax,rightmax)-arr[t];
            t++;
        }
        return total;
    }
}
```

# Complexty Analysis

Time:O(n)

Space:O(n)
