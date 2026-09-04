# Coin change 2

# Recurrsion

```
 class Solution {
    int find(int arr[],int target,int indx){
          if(target==0){
            return 1;
        }
        if(indx==0){
            if(target%arr[0]==0){
                return 1;
            }
            return 0;
        }
        int nottake=find(arr,target,indx-1);
        int take=0;
        if(arr[indx]<=target){
            take=find(arr,target-arr[indx],indx);
        }
        return take+nottake;
    }
    public int change(int target, int[] arr) {
        int ans=find(arr,target,arr.length-1);
        if(ans==0){
            return 0;
        }
        return ans;
    }
}
```

# Memoisation

```
class Solution {
    int find(int arr[],int target,int indx,int dp[][]){
          if(target==0){
            return 1;
        }
        if(indx==0){
            if(target%arr[0]==0){
                return 1;
            }
            return 0;
        }
       if(dp[indx][target]!=-1){
         return dp[indx][target];
       }
        int nottake=find(arr,target,indx-1,dp);
        int take=0;
        if(arr[indx]<=target){
            take=find(arr,target-arr[indx],indx,dp);
        }
        return dp[indx][target]=take+nottake;
    }
    public int change(int target, int[] arr) {
        int dp[][]=new int[arr.length][target+1];
        for(int i=0;i<arr.length;i++){
            Arrays.fill(dp[i],-1);
        }
        int ans=find(arr,target,arr.length-1,dp);
        if(ans==0){
            return 0;
        }
        return ans;
    }
}
```

# Tabulation
```

  public int change(int target, int[] arr) {
       int dp[][]=new int[arr.length][target+1];
      for(int i = 0; i < arr.length; i++) {
        dp[i][0] = 1;
    }

    // Using only arr[0]
    for(int j = 0; j <= target; j++) {
        if(j % arr[0] == 0) {
            dp[0][j] = 1;
        }
    }
       for(int i=1;i<arr.length;i++){
        for(int j=1;j<=target;j++){
            int nottake=dp[i-1][j];
            int take=0;
            if(arr[i]<=j){
            take=dp[i][j-arr[i]];
            }
            dp[i][j]=take+nottake;
        }
       }
       return dp[arr.length-1][target];
    }
}

```

# Optimal

```
 public int change(int target, int[] arr) {
       int prev[]=new int[target+1];
     for(int j = 0; j <= target; j++) {
    if(j % arr[0] == 0) {
        prev[j] = 1;
    }
}
       for(int i=1;i<arr.length;i++){
        int curr[]=new int[target+1];
        curr[0]=1;
        for(int j=1;j<=target;j++){
            int nottake=prev[j];
            int take=0;
            if(arr[i]<=j){
            take=curr[j-arr[i]];
            }
            curr[j]=take+nottake;
        }
        prev=curr;
       }
       return prev[target];
    }
}
```
