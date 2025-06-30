# Math Square root using binary search

```
class Solution {
    public static int fun(int mid){
        return mid*mid;
    }
    public long floorSqrt(long n) {
      int low=1;
      int high=(int)n;
      long ans=-1;
      while(low<=high){
        int mid=(low+high)/2;
        int find=fun(mid);
         if(find>n){
            high=mid-1;
         }
         else{ //if(find<=n)
            ans=(long)mid;
            low=mid+1;
         }
      }
      return ans;
    }
}
```

# Complexities

Time:O(log N)

Space:O(1)

