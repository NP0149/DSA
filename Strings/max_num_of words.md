# 1752. Check if Array Is Sorted and Rotated
[Problem Link](https://www.geeksforgeeks.org/problems/second-largest3735/1)

## Approach - 1

1. To check the array is sorted and rotated
2. We have two observations
   - 3 4 5 1 2 => there should one breaking point which breaks the sorting order
     - here we can see that the breaking point is 5 and 1
   - 1 2 3 4 5 => Here there is no breaking point
   - 2 1 3 4 => according to first approach, it accepts, but it is not in ascending order
   - If the array is rotated, the last element of rotated array should be less than first element of rotated array
3. Use count variable, which increments when we get breaking points while traversing
4. If at any instance the count variable becomes greater than one return false, means the given array is not sorted and rotated

```Java

class Solution {
public:
    bool check(vector<int>& nums) {
       int count = 0;
       for(int i=0;i<nums.size();i++){
           if(nums[i]>nums[(i+1)%nums.size()])
                count++;
            if(count>1)
                return false;
       }
       return true;
    }


};

```

## Complexity Analysis:

### Time Complexity: O(N)

### Space Complexity: O(1)
