# Is bad version

[Problem Link](https://leetcode.com/problems/first-bad-version/submissions/1711682359/)

# Approach-I

1)normal binary search,but when we got isbadversion()=true then we need to move left to find the least one

2)high=mid-1;

```
/* The isBadVersion API is defined in the parent class VersionControl.
      boolean isBadVersion(int version); */

public class Solution extends VersionControl {
    public int firstBadVersion(int n) {
        int low=1;
        int high=n;
        while(low<=high){
            int mid=low+(high-low)/2;
            if(isBadVersion(mid)==true){
                high=mid-1;
            }
            else{
                low=mid+1;
            }
        }
        return low;
    }
}
```
# Complexities

Time:O(log n)

Space:O(1)
