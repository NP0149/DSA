# Candy distribution among children

[Problem Link](https://leetcode.com/problems/candy/submissions/1859722205/)


```
class Solution {
     public int candy(int[] arr) {
      int sum=0;
       int rightn[]=new int[arr.length];
          int n=arr.length;
          rightn[n-1]=1;
          int val=1;
          for(int i=n-2;i>=0;i--){
           
              if(arr[i]>arr[i+1]){
                  val=val+1;
                  rightn[i]=val;
              }
              else{
                rightn[i]=1;
                val=1;
              }
          }
           int val1=1;
        int leftn[]=new int[arr.length];
        leftn[0]=val1;
        for(int i=1;i<arr.length;i++){
            if(arr[i]>arr[i-1]){
                val1++;
                leftn[i]=val1;
            }
            else{
             leftn[i]=1;
             val1=1;
            }
        }
      for(int i=0;i<arr.length;i++){
          arr[i]=Math.max(leftn[i],rightn[i]); 
          sum+=arr[i] ;
      }
      return sum;
    }
}
```
# Complexity Analysis

Time:O(n)

Space:O(n)
