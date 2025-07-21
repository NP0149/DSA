# Maximum consecutive ones-III

[Problem Link](https://leetcode.com/problems/max-consecutive-ones-iii/description/)

# Approach-I

Given a binary array nums and an integer k, return the maximum number of consecutive 1's in the array if you can flip at most k 0's

```
class Solution {
    public int longestOnes(int[] arr, int k) {
      int n=arr.length;
      int l=0;
      int ans=-1;
      int temp=0;
      for(int i=0;i<n;i++){
        if(arr[i]==0){
            temp++;
        }
        while(temp>k){
            if(arr[l]==0){
                temp--;
            }
            l++;
        }
      ans=Math.max(ans,i-l+1);
      }
 return ans;
    }
    }
```

# Complexities

Time:O(n)

Space:O(1)
