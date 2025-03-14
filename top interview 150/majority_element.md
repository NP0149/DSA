# Majority Element



[Problem Link](https://leetcode.com/problems/majority-element/description/?envType=study-plan-v2&envId=top-interview-150)

# Approach I
```
 class Solution {
    public int majorityElement(int[] arr) {
        int count=0;
        int maxcount=-1;
        int a=-1;
        int n=arr.length;
        int candidate=0;
        int repeat=0;
        for(int i=0;i<n;i++){
             if(count==0){
                 candidate=arr[i];
            }
            if(arr[i]==candidate){
                count++;
            }
            else{
                count--;
            }
        }
         
         for(int i=0;i<n;i++){
            if(candidate==arr[i])
            repeat++;
         }
         if(repeat>n/2){
            a=candidate;
         }
         return a;
    }
        
}
```


# Approach II

```
 HashMap<Integer,Integer> repeat=new HashMap<>();
        for(int i=0;i<arr.length;i++){
            int  k=arr[i];
            if(repeat.containsKey(k)){
                int prev=repeat.get(k);
                repeat.put(k,prev+1);
            }
            else{
                repeat.put(k,1);
            }
        }
        int major=0;
        for(int ki:repeat.keySet()) {
            if (repeat.get(ki) > arr.length / 2)
                major = ki;

        }
        return major;

```
