# Maximum circular sub array sum

[Problem Link](https://www.geeksforgeeks.org/problems/max-circular-subarray-sum-1587115620/1)


```
class Solution {
    public int maxCircularSum(int arr[]) {
       int maxsum=arr[0];
       int currsum=arr[0];
       int minsum=arr[0];
       int curr_min_sum=arr[0];
       int total=0;
       for(int i=0;i<arr.length;i++){
           total+=arr[i];
           if(i>0){
               currsum=Math.max(arr[i],currsum+arr[i]);
               maxsum=Math.max(maxsum,currsum);
               
               curr_min_sum=Math.min(arr[i],curr_min_sum+arr[i]);
               minsum=Math.min(minsum,curr_min_sum);
           }
       }
       if(maxsum<0){
           return maxsum;
       }
       return Math.max(maxsum,total-minsum);
    }
}

```
