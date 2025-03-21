# Array partition

[Problem Link](https://leetcode.com/problems/array-partition/)


# Approach-I

1)sort the array the best pairs will be the adjacent pairs in the sorted array so pick the small one among and then sum them
return the sum

```
class Solution {
    public int arrayPairSum(int[] arr) {
         int n = arr.length;
        int m = n / 2;
        int k = n / m;
        Arrays.sort(arr);
        int l = 0;
        int sum=0;
        for (int i = 0; i < n; i++) {
           if(i%2==0){
               sum+=arr[i];
           }
        }
       return sum;
}
}
```

# Complexity Analysis

Time:O(N logN);

Space:O(1);
