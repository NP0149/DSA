# Need to make max frequency in an array

[Problem Link](https://www.geeksforgeeks.org/problems/maximum-frequency-1662528911/1)


```
class Solution {
    public int maxFrequency(int[] arr, int k) {
        // code here
        Arrays.sort(arr);
        int l=0;
        long sum=0;
        int ans=-1;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
            long cost=(long)arr[i]*(i-l+1)-sum;
            while(cost>k){
                sum-=arr[l];
                l++;
                cost=(long)arr[i]*(i-l+1)-sum;
            }
            ans=Math.max(ans,i-l+1);
        }
        return ans;
    }
}
```
