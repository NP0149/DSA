# Majority element greater than n/3

[Problem Link](https://leetcode.com/problems/majority-element-ii/)

```
class Solution {
    public List<Integer> majorityElement(int[] arr) {
        HashMap<Integer,Integer> hm=new HashMap<>();
        int n=arr.length;
        int k=n/3;
        for(int num:arr){
            if(hm.containsKey(num)){
                int prev=hm.get(num);
                hm.put(num,prev+1);
            }
            else{
                hm.put(num,1);
            }
        }
        List<Integer> l=new ArrayList<>();
        for(int num:hm.keySet()){
            if(hm.get(num)>k){
               l.add(num);
            }
        }
        return l;
    }
}
```

# Complexities

Time:O(n);

Space:O(n);
