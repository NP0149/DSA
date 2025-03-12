# Remove duplicate II

[Problem Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/description/?envType=study-plan-v2&envId=top-interview-150)

```
 class Solution {
    public static int removeDuplicates(int[] nums) {
        if (nums.length <= 2) return nums.length;

        int index = 2; 

        for (int i = 2; i < nums.length; i++) {
            if (nums[i] != nums[index - 2]) { 
                nums[index] = nums[i];
                index++;
            }
        }

        return index; 
    }
}
```
