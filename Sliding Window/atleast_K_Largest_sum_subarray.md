# Largest sum of sub array whose length is atleast k

[Problem Link](https://www.geeksforgeeks.org/problems/largest-sum-subarray-of-size-at-least-k3121/1)

```
// User function Template for Java

class Solution {

    public long maxSumWithK(long a[], long n, long k) {
        
        long prevmax[]=new long[a.length];
        prevmax[0]=a[0];
        for(int i=1;i<a.length;i++){
            prevmax[i]=Math.max(a[i],prevmax[i-1]+a[i]);
        }
        long windowsum=0;
        for(int i=0;i<(int)k;i++){
            windowsum+=a[i];
        }
        long ans=windowsum;
        for(int i=(int)k;i<a.length;i++){
            windowsum+=a[i]-a[i-(int)k];
            ans=Math.max(ans,windowsum);
            ans=Math.max(ans,windowsum+prevmax[i-(int)k]);
        }
        return ans;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
