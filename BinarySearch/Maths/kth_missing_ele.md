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

# Approach-II

```
class Solution {
    public int findKthPositive(int[] arr, int k) {
        int n=arr.length;
        int low=0;
        int high=n-1;
        int i=0;
        while(low<=high){
            int mid=(low+high)/2;
            int missing=arr[mid]-(mid+1);
            if(missing<k){
                low=mid+1;
            }
            else{
                high=mid-1;
            }
        }
        return low+k;
    }
}
```

# Complexities

Time:O(log n)

Space:O(1)
