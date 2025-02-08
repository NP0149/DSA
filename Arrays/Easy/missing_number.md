# MISSING NUMBER IN A ARRAY
[PROBLEM LINK](https://leetcode.com/problems/missing-number/)

APPROCH-I
1)consider the length of the array 
2)if the length of the array is n then n numbers should be present in that array
consider the test case[0,1] then there are two elements in the array so the range of the elements should be [0,2]
3)so consider the sum of all elements in the array and store them in some constant(sum1) and find the other sum and then store in other variable
(sum2);
4)the difference between sum1 and sum2 will become the missing variable
```Java
class Solution {
    public int missingNumber(int[] nums) {
        int sum1=0;
        int sum2=0;
        int max=-1;
        int k;
       int n=nums.length;
        for(int i=0;i<n;i++){
            sum1=sum1+nums[i];
        }
        sum2=(n*(n+1))/2;
         k=sum2-sum1;
         return k;
    }

}
```
# time complexity:O(N)
