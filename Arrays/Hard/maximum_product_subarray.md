# Maximum product subarray

[Problem Link](https://leetcode.com/problems/maximum-product-subarray/submissions/1846384083/)


# optimal approach

```
class Solution {
    public int maxProduct(int[] arr) {
        int maxpro=arr[0];
        int minpro=arr[0];
        int ans=arr[0];
        for(int i=1;i<arr.length;i++){
            int curr=arr[i];
            if(curr<0){
             int temp=maxpro;
             maxpro=minpro;
             minpro=temp;
            }
            maxpro=Math.max(maxpro*curr,curr);
            minpro=Math.min(minpro*curr,curr);
            ans=Math.max(maxpro,ans);
        }
        return ans;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)

# OPtimal appoarch-II

```
class Solution {
    public int maxProduct(int[] arr) {
       int ans=Integer.MIN_VALUE;
       int ps=1;
       int sf=1;
       int n=arr.length;
       for(int i=0;i<arr.length;i++){
         if(ps==0){
            ps=1;
         }
         if(sf==0){
            sf=1;
         }
         ps=ps*arr[i];
         sf=sf*arr[n-i-1];
        ans=Math.max(ans,Math.max(ps,sf));
       }
       return ans;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(1)

