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
    }
}
```

# Memoisation ,tabulation and optimal approach


```
class Solution {
    static boolean find(int arr[],int indx,int target){
        if(target==0){
            return true;
        }
        if(indx<0){
            return false;
        }
        if(indx==0){
            return arr[0]==target;
        }
        boolean nottake=find(arr,indx-1,target);
        boolean take=false;
        if(arr[indx]<=target){
            take=find(arr,indx-1,target-arr[indx]);
        }
        return (take || nottake);
    }
    static boolean find_mem(int arr[],int indx,int target,int dp[][]){
        if(target==0){
            return true;
        }
        if(indx<0){
            return false;
        }
        if(indx==0){
            return arr[0]==target;
        }
      if(dp[indx][target]!=-1){
        return dp[indx][target]==1;
      }
      boolean nottake=find_mem(arr,indx-1,target,dp);
      boolean take=false;
      if(arr[indx]<=target){
        take=find_mem(arr,indx-1,target-arr[indx],dp);
      }
      dp[indx][target]=(take || nottake)?1:0;
      return dp[indx][target]==1;
    }
    static boolean find_tab(int arr[],int target){
        boolean dp[][]=new boolean[arr.length][target+1];
       for(int i=0;i<arr.length;i++){
        dp[i][0]=true;
       }
       if(arr[0]<=target){
        dp[0][arr[0]]=true;
       }
       for(int i=1;i<arr.length;i++){
        for(int j=1;j<=target;j++){
            boolean nottake=dp[i-1][j];
            boolean take=false;
            if(arr[i]<=j){
           take=dp[i-1][j-arr[i]];
            }
            dp[i][j]=(take || nottake);
        }
       }
       return dp[arr.length-1][target];
    }
    static boolean find_opt(int arr[],int target){
        boolean prev[]=new boolean[target+1];
        prev[0]=true;
        if(arr[0]<=target){
            prev[arr[0]]=true;
        }
         for(int i=1;i<arr.length;i++){
            boolean curr[]=new boolean[target+1];
            for(int j=1;j<=target;j++){
                boolean nottake=prev[j];
                boolean take=false;
                if(arr[i]<=j){
                   take= prev[j-arr[i]];
                }
                curr[j]=(take || nottake);
            }
            prev=curr;
         }
     return prev[target];
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
    //  int dp[][]=new int[arr.length][target+1];
    //     for(int a[]:dp){
    //         Arrays.fill(a,-1);
    //     }
    //     return find_mem(arr,arr.length-1,target,dp);
//    return find_tab(arr,target);
 return find_opt(arr,target);
    }
}
```


