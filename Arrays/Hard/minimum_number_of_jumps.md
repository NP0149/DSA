# Minimum number of jumps

[Problem Link](https://www.geeksforgeeks.org/problems/minimum-number-of-jumps-1587115620/1)


```
class Solution {
    public int minJumps(int[] arr) {
     if(arr[0]==0){
         return -1;
     }
     int far=0;
     int currend=0;
     int jumps=0;
     for(int i=0;i<arr.length;i++){
         far=Math.max(far,i+arr[i]);
         if(i==currend){
             jumps++;
             currend=far;
             if(currend>=arr.length-1){
                 return jumps;
             }
             if(currend==i){
                 return -1;
             }
         }
     }
     return jumps;
    }
}
```
