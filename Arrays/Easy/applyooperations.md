# Apply operations on array

[problem link](https://leetcode.com/problems/apply-operations-to-an-array/?envType=daily-question&envId=2025-03-01)


```
class Solution {
    public int[] applyOperations(int[] nums) {
        int n=nums.length;
        for(int i=0;i<n-1;i++){
            if(nums[i]==nums[i+1]){
                nums[i]=nums[i]*2;
                nums[i+1]=0;
            }
        }
        int t=0;
        for(int i=0;i<n;i++){
            if(nums[i]!=0){
                        nums[t]=nums[i];
                        t++;
            }
        }
        while(t<n){
            nums[t]=0;
            t++;
        }
        return nums;

    }
}
```
