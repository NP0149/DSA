[Problem Link](https://www.geeksforgeeks.org/problems/modify-array-to-maximize-sum-of-adjacent-differences1729/1)


```
class Solution {
    public int maxDiffSum(int[] arr) {
      int dp[][]=new int[arr.length][2];
      dp[0][0]=0;
      dp[0][1]=0;
      for(int i=1;i<arr.length;i++){
          dp[i][0]=Math.max(dp[i-1][0]+Math.abs(arr[i]-arr[i-1]),dp[i-1][1]+Math.abs(arr[i]-1));
          dp[i][1]=Math.max(dp[i-1][0]+Math.abs(arr[i-1]-1),dp[i-1][1]+Math.abs(1-1));
      }
      return Math.max(dp[arr.length-1][0],dp[arr.length-1][1]);
    }
}
```
```
class Solution {
    
     int find(int arr[],int i,int prev){
         if(i>=arr.length){
             return 0;
         }
         int startorg=Math.abs(arr[i]-prev)+find(arr,i+1,arr[i]);
         int startone=Math.abs(1-prev)+find(arr,i+1,1);
         return Math.max(startone,startorg);
     }
    public int maxDiffSum(int[] arr) {
       int startorg=find(arr,1,arr[0]);
       
       int startone=find(arr,1,1);
       return Math.max(startorg,startone);
    }
}
```
