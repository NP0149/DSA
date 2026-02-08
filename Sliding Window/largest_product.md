# Largest Product sub array

[Problem Link](https://www.geeksforgeeks.org/problems/largest-product/1)

```
/*You are required to complete the function*/
class Solution {
    public int findMaxProduct(int[] arr, int k) {
        // code here
        int l=0;
        int ans=Integer.MIN_VALUE;
        int pro=1;
        for(int i=0;i<arr.length;i++){
            pro*=arr[i];
            if(i-l>k-1){
                pro=pro/arr[l];
                l++;
            }
            if(i-l==k-1){
                ans=Math.max(pro,ans);
            }
        }
        return ans;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)
