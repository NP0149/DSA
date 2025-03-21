# Sub array sum greater than threshold 

[Problem Link](https://leetcode.com/problems/number-of-sub-arrays-of-size-k-and-average-greater-than-or-equal-to-threshold/)


# Approach-I

1)consider all sub arrays and sub array sums and then compare the average of sum with threshold if greater just increase the count

```
class Solution {
    public int numOfSubarrays(int[] arr, int k, int threshold) {
        int count=0;
        int n=arr.length;
        for(int i=0;i<n-k+1;i++){
            int j=i+k-1;
            int sum=0;
            for(int t=i;t<=j;t++){
             sum+=arr[t];
             }
             if(sum/k>=threshold){
                 count++;
            }
        }
    return count;
 }
}

```

# Complexity Analysis

Time:O(Nk);

Space:O(1);
