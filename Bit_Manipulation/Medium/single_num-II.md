# Single number II
[Problem Link](https://leetcode.com/problems/single-number-ii/description/)
# Approach-I

1)every element in the array repeats thrice except one so we need to find that one particular number

2) every time compare arr[i] and arr[i-1] and then jump by 3 steps

```
class Solution {
    public int singleNumber(int[] arr) {
        Arrays.sort(arr);
        int n=arr.length;
        for(int i=1;i<arr.length;i=i+3){
            if(arr[i]!=arr[i-1]){
                return arr[i-1];
            }
        }
        return arr[n-1];
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)

