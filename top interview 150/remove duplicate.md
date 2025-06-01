# Removing duplicate element


[Problem Link](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/?envType=study-plan-v2&envId=top-interview-150)

# Approach-I

```
class Solution {
    public int removeDuplicates(int[] nums) {
       int k=1;
        for(int i=1;i<nums.length;i++){
            if(nums[i]!=nums[i-1]){
                nums[k]=nums[i];
                k++;
            }
        }
        return k;
        }
    }
```
# Complexities

Time:O(n);

Space:O(1);

# Approach-II

hashset only accepts unique elements

```
import java.util.*;
public class unique {
    public static void main(String args[]) {
        int nums[] = {1,1,2};
        HashSet<Integer> hs = new HashSet<>();
        for (int num : nums) {
            hs.add(num);
        }
        int uni[] = new int[hs.size()];
        int i = 0;
        for (int num : hs) {
            uni[i++] = num;
        }
        nums = Arrays.copyOf(uni, uni.length);
        System.out.println(uni.length);
        for(int num:nums){
            System.out.print(num+" ");
        }
        System.out.println();
        System.out.println(nums.length);
    }
}
```

# Complexities

Time:O(nlogn)//due to sorting

Space:O(n)//due to hashset

