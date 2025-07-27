# Candies Distribution to k childern equally

[Problem Link](https://leetcode.com/problems/maximum-candies-allocated-to-k-children/submissions/1713411180/)

# Approach-I

```
class Solution {
    public static long fun(int arr[],long m,long mid){
        int n=arr.length;
        long count=0;
        for(int i=0;i<n;i++){
            count+=(long)arr[i]/mid;
        }
        if(count>=m){
            return 1;
        }
        else{
            return 0;
        }
    }
    public int maximumCandies(int[] arr, long k) {
        long low=1;
        long ans=-1;
        long sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
     long high=sum;
        if(sum<k){
            return 0;
        }
       
        while(low<=high){
            long mid=low+(high-low)/2;
         long t=fun(arr,k,mid);
            if(t==1){
                ans=mid;
              low=mid+1;
            }
            else{
              high=mid-1;
            }
        }
        return (int)ans;
    } 
}
```

# Complexities

Time:O(n * log(sum))

Space:O(1)
