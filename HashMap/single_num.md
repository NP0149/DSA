# Singly occured number 

[Problem Link](https://leetcode.com/problems/single-number/submissions/1652448168/)

```
class Solution {
    public int singleNumber(int[] nums) {
        HashMap<Integer,Integer> hm=new HashMap<>();
        int n=nums.length;
        for(int i=0;i<n;i++){
            if(hm.containsKey(nums[i])){
                int prev=hm.get(nums[i]);
                hm.put(nums[i],prev+1);
            }
            else{
                hm.put(nums[i],1);
            }
        }
        int m=0;
        for(int num:hm.keySet()){
           if(hm.get(num)==1){
            m=num;
           }
        }
        return m;
    }
}
```

# Complexities

Time:O(n);

Space:O(n);//hashmap
