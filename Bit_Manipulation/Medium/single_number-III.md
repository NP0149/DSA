# Single number III

[Problem Link](https://leetcode.com/problems/single-number-iii/)

# Approach-I

1)first find all the elements in the array and u will get a number n

2)find the first set bit for n and then consider two buckets setone and nonsetone

3)in a number if a particular number set then add it to the setone else add to nonsetone

4)add two array and then return the array

```
class Solution {
    static int find_firstsetbit(int n){
        for(int i=0;i<32;i++){
            if(((n>>i)&1)==1){
                return i;
            }
        }
        return 0;
    }
    static int find(int n,int i){
        return (n>>i)&1;
    }
    public int[] singleNumber(int[] arr) {
        int n=0;
        for(int i=0;i<arr.length;i++){
            n=n^arr[i];
        }
        int first_setbit=find_firstsetbit(n);
        int ones=0,twos=0;
        for(int i=0;i<arr.length;i++){
           int m=find(arr[i],first_setbit);
           if(m==1){
            ones=ones^arr[i];
           }
           else{
            twos=twos^arr[i];
           }
        }
        int s[]=new int[2];
        s[0]=ones;
        s[1]=twos;
        return s;
    }
}
```

# Complexity Analysis

Time:O(n)

Space:O(1)

