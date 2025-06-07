# kadanes algorithm

[Problem Link](https://leetcode.com/problems/maximum-subarray/description/?envType=study-plan-v2&envId=top-interview-150)

```
class Solution {
    public int maxSubArray(int[] arr) {
        int n=arr.length;
        int maxsum=Integer.MIN_VALUE;
        int sum=0;
        if(arr.length==1){
            return arr[0];
        }
        for(int i=0;i<n;i++){
              sum+=arr[i];
               maxsum=Math.max(maxsum,sum);
              if(sum<0){
                sum=0;
              }
        }
        return maxsum;
    }
}
```

# Complexties

Time:O(n);

Space:O(1);
