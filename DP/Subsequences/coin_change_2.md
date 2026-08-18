# Coin change 2

# Recurrsion

```
class Solution {
    static int find_rec(int arr[],int indx,int target){
        if(indx==0){
           if(target%arr[0]==0){
            return 1;
           }
           else{
            return 0;
           }
        }
        if(target==0){
            return 1;
        }
        int nottake=find_rec(arr,indx-1,target);
        int take=0;
        if(arr[indx]<=target){
            take=find_rec(arr,indx,target-arr[indx]);
        }
        return take+nottake;
    }
    public int change(int target, int[] arr) {
      int ans=find_rec(arr,arr.length-1,target);
     return ans;
    }
}
```

# Memoisation

```
class Solution {
    static int find_rec(int arr[],int indx,int target,int dp[][]){
        if(indx==0){
           if(target%arr[0]==0){
            return 1;
           }
           else{
            return 0;
           }
        }
        if(target==0){
            return 1;
        }
        if(dp[indx][target]!=-1){
            return dp[indx][target];
        }
        int nottake=find_rec(arr,indx-1,target,dp);
        int take=0;
        if(arr[indx]<=target){
            take=find_rec(arr,indx,target-arr[indx],dp);
        }
        return dp[indx][target]=take+nottake;
    }
    public int change(int target, int[] arr) {
        int dp[][]=new int[arr.length][target+1];
        for(int a[]:dp){
            Arrays.fill(a,-1);
        }
      int ans=find_rec(arr,arr.length-1,target,dp);
     return ans;
    }
}
```

# Tabulation
```

```
