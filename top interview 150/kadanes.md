# kadanes algorithm

```
 class Solution {
    public int maxSubArray(int[] nums) {
        int maxsubarrsum=-1000000000;
        int subarrsum=0;
        for(int i=0;i<nums.length;i++){
            subarrsum=subarrsum+nums[i];
            maxsubarrsum=Math.max(subarrsum,maxsubarrsum);
            if(subarrsum<0)
            subarrsum=0;
        }
        return maxsubarrsum;
    }
    }
```
