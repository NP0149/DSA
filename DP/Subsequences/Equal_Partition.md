# Equal Partition 

[Problem Link](https://leetcode.com/problems/partition-equal-subset-sum/)


# Recurrsion

```
class Solution {
    static boolean isSubsetSum(int arr[], int sum) {
       boolean dp[][]=new boolean[arr.length][sum+1];
       for(int i=0;i<arr.length;i++){
           dp[i][0]=true;
       }
       if(arr[0]<=sum){
           dp[0][arr[0]]=true;
       }
       for(int i=1;i<arr.length;i++){
           for(int j=1;j<=sum;j++){
               if(arr[i]<=j){
                   dp[i][j]=dp[i-1][j] || dp[i-1][j-arr[i]];
               }
               else{
                   dp[i][j]=dp[i-1][j];
               }
           }
       }
      return dp[arr.length-1][sum];
    }
}
```

```
class Solution {
    static boolean find(int arr[],int i,int n,int target,int sum){
        if(sum==target){
            return true;
        }
        if(i>=n){
            return false;
        }
        if(find(arr,i+1,n,target,sum+arr[i])){
            return true;
        }
        if(find(arr,i+1,n,target,sum)){
            return true;
        }
        return false;
    }
    public boolean canPartition(int[] arr) {
        int n=arr.length;
        int sum=0;
        for(int i=0;i<n;i++){
            sum+=arr[i];
        }
       int target=sum/2;
       if(sum%2==0){
        return find(arr,0,n,target,0);
       }
       else{
        return false;
       }
    }
}
```

# Complexity Analysis

Time:O(2^n)

Space:O(n)

# Memoisation

```
class Solution {
    int find(int arr[],int indx,int target,int dp[][]){
        if(target==0){
            return 1;
        }
        if(indx==0){
            if(arr[0]==target){
                return 1;
            }
            else{
                return 0;
            }
        }
        if(dp[indx][target]!=-1){
            return dp[indx][target];
        }
        int nottake=find(arr,indx-1,target,dp);
        int take=0;
       if(arr[indx]<=target){
        take=find(arr,indx-1,target-arr[indx],dp);
       }
       return dp[indx][target]=(take==1 || nottake==1)?1:0;
    }
    public boolean canPartition(int[] arr) {
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        if(sum%2==1){
            return false;
        }
        int target=sum/2;
        int dp[][]=new int[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
            Arrays.fill(dp[i],-1);
        }
        return  find(arr,arr.length-1,target,dp)==1;
```
# Tabulation
```
class Solution {
    public boolean canPartition(int[] arr) {
        int sum=0;
        for(int i=0;i<arr.length;i++){
            sum+=arr[i];
        }
        if(sum%2==1){
            return false;
        }
        int target=sum/2;
        boolean dp[][]=new boolean[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
            dp[i][0]=true;
        }
        if(arr[0]<=target){
            dp[0][arr[0]]=true;
        }
        for(int i=1;i<arr.length;i++){
            for(int j=1;j<=target;j++){
                if(arr[i]<=j){
                    dp[i][j]=dp[i-1][j] || dp[i-1][j-arr[i]];
                }
                else{
                    dp[i][j]=dp[i-1][j];
                }
            }
        }
        return dp[arr.length-1][target];
    }
}
```


