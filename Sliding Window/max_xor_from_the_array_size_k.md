# Maximum XOR from the sub array K

[Problem Link](https://www.geeksforgeeks.org/problems/max-xor-subarray-of-size-k/1)

```
class Solution {
    public int maxSubarrayXOR(int[] arr, int k) {
        // code here
        int l=0;
        int val=0;
        int maxvalue=Integer.MIN_VALUE;
        for(int i=0;i<arr.length;i++){
            val=val^arr[i];
            if(i-l>k-1){
                val=val^arr[l];
                l++;
            }
            if(i-l==k-1){
                maxvalue=Math.max(maxvalue,val);
            }
        }
        return maxvalue;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
