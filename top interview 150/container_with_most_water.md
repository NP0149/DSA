# container with most water

[Problem Link](https://leetcode.com/problems/container-with-most-water/)

# Approach

1)it is mainly a two pointer approch

2)left pointer at index 0 and right pointer at index length-1 

3)here we can observe that if there is a minimum value at left index then left++if not right--..

```
class Solution {
    public int maxArea(int[] arr) {
         int n=arr.length;
      int maxwater=0;
      int lp=0;
      int rp=n-1;
      while(lp<rp){
        int w=rp-lp;
        int h=Math.min(arr[lp],arr[rp]);
        int water=w*h;
        maxwater=Math.max(water,maxwater);
        if(arr[lp]<arr[rp]){
            lp++;
        }
        else{
            rp--;
        }
      }
       return maxwater;  
        
    }
}
```

# complexities

Time complexity:O(N);

space complexity:O(1);
