# Minimum size subarray

[Problem Link](https://leetcode.com/problems/minimum-size-subarray-sum/)

```
class Solution {
    public int minSubArrayLen(int target, int[] arr) {
        int l=0;
        int n=arr.length;
        int sum=0;
        int count=0;
        int ans=Integer.MAX_VALUE;
        int temp=0;
        for(int i=0;i<n;i++){
            temp+=arr[i];
        }
        if(temp<target){
            return 0;
        }
        for(int i=0;i<n;i++){
           sum+=arr[i];
            while(sum>=target && l<=i){
                ans=Math.min(ans,i-l+1);
                sum-=arr[l];
                l++;
            }
        }
        return ans;
    }
}
```

# Complexitiy Analysis 

Time:O(n)

Space:O(1)
