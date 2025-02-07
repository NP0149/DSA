# Largest Element in Array

[Problem Link]([https://www.geeksforgeeks.org/problems/largest-element-in-array4009/0](https://leetcode.com/problems/max-consecutive-ones/description/))

## Approach - 1

1.use a sum variable, when ever we get a zero then simply change sum to zero.
    find the max sum and return it


```Java

class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int count=0;
        int t=0;
        for(int i=0;i<nums.length;i++){
            if(nums[i]==1)
            t++;
            else
            {
                count=Math.max(count,t);
                t=0;
            }
        }
        count=Math.max(count,t);
        return count;
    }
}
      
```

## Complexity Analysis:

### Time Complexity: O(N)

### Space Complexity: O(1)

