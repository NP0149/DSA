# Kth missing element

[Problem Link](https://leetcode.com/problems/kth-missing-positive-number/)

# Approach-I(Brute)

```
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int count=1;
  for(int i=0;i<arr.length;i++){
    if(arr[i]<=k){
        k++;
    }
    else{
        break;
    }
  }
  return k;
    }
}
```
# Complexities

Time:O(n)

Space:O(1)
