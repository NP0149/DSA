# maximum circular sub array sum

[Problem Link](https://leetcode.com/problems/maximum-sum-circular-subarray/?envType=study-plan-v2&envId=top-interview-150)


## traverse the array by twice kadanes find max sum if maxsum<0 just return maxsum and if not find minsum too and then return Max(maxsum,total-minsum)

```
class Solution {
    public int maxSubarraySumCircular(int[] arr) {
        int currsum=0;
        int maxsum=Integer.MIN_VALUE;
        int minsum=Integer.MAX_VALUE;
        int currminsum=0;
        int total=0;
       for(int i=0;i<arr.length;i++){
         currsum+=arr[i];
         if(currsum<arr[i]){
            currsum=arr[i];
         }
         maxsum=Math.max(maxsum,currsum);
         
         currminsum+=arr[i];
         if(currminsum>arr[i]){
            currminsum=arr[i];
         }
       minsum=Math.min(minsum,currminsum);

       total+=arr[i];
       }
       System.out.println(minsum);
       System.out.println(maxsum);
       if(maxsum<0){
        return maxsum;
       }
       return Math.max(maxsum,total-minsum);
    }
}
```
