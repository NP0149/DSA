# Majority Element



[Problem Link](https://leetcode.com/problems/majority-element/description/?envType=study-plan-v2&envId=top-interview-150)
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
