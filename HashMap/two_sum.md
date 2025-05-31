# two sum

[Problem Link](https://leetcode.com/problems/two-sum/description/)

# Approach-I

1)create a hashmap then 
2)add all the array elements into hashmap like key as number and the valuse is index
3)everytime do target-arr[i],name it as partner then you will get the required number to reach target and then search for the key partner
4)if partner is there in the hashmap ,store the indexes in arrays and then return them

```
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int store[]=new int[2];
        int n=nums.length;
        int prev=0;
        HashMap<Integer,Integer> hm=new HashMap<>();
        for(int i=0;i<n;i++){
            int partner=target-nums[i];
            if(hm.containsKey(partner)){
                store[0]=i;
                store[1]=hm.get(partner);
            }
            else{
                hm.put(nums[i],prev);
                prev++;
            }
        }
        return store;
    }
}
       

```

# Complexities

Time:O(n); //n is the number of elements in the hashmap

Space:O(n);
