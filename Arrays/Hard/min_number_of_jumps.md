# Minimum number of jumps to reach end

[Problem Link](https://www.geeksforgeeks.org/problems/minimum-number-of-jumps-1587115620/1)


```
class Solution {
    int find(int arr[],int indx,int dp[]){
        if(indx>=arr.length-1){
            return 0;
        }
        if(arr[indx]==0){
            return Integer.MAX_VALUE;
        }
        if(dp[indx]!=-1){
            return dp[indx];
        }
      int min=Integer.MAX_VALUE;
      for(int j=1;j<=arr[indx];j++){
          
          if(indx+j<arr.length){
              
          int ans=find(arr,indx+j,dp);
          if(ans!=Integer.MAX_VALUE){
          min=Math.min(min,ans+1);
          }
          }
          dp[indx]=min;
      }
      return dp[indx]=min;
    }
    public int minJumps(int[] arr) {
        int dp[]=new int[arr.length];
        Arrays.fill(dp,-1);
      if(arr[0]==0){
          return -1;
      }
      int ans=find(arr,0,dp);
      if(ans==Integer.MAX_VALUE){
          return -1;
      }
      return ans;
    }
}
```
