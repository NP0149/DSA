# Frog jump with k steps

# Using recurrsion

```
  static int find(int arr[],int indx,int k) {
        if (indx == 0) {
            return 0;
        }
        int min_energy=Integer.MAX_VALUE;
        for(int i=1;i<=k;i++){
            if(indx-i>=0){
             int jump=find(arr,indx-i,k)+Math.abs(arr[indx]-arr[indx-i]);
             min_energy=Math.min(min_energy,jump);
            }
        }
        return min_energy;
    }
```
# Complexities

Time:O(k^n)

Space:O(n)

# Using Memoization

```
  static int find_mem(int dp[],int arr[],int indx,int k){
        if(indx==0){
            return 0;
        }
        if(dp[indx]!=-1){
            return dp[indx];
        }
        int min_energy=Integer.MAX_VALUE;
        for(int i=1;i<=k;i++){
            if(indx-i>=0){
                int jump=find_mem(dp,arr,indx-i,k)+Math.abs(arr[indx]-arr[indx-i]);
                min_energy=Math.min(min_energy,jump);
            }
        }
        dp[indx]=min_energy;
        return dp[indx];
    }
```
# Complexities

Time:O(k*n)

Space:O(n)

# Using Tabulation

```
 static int find_tab(int dp[],int arr[],int indx,int k){
      dp[0]=0;
      for(int i=1;i<dp.length;i++){
          int min_energy=Integer.MAX_VALUE;
          for(int j=1;j<=k;j++){
              if(i-j>=0) {
                  int jump = dp[i - j] + Math.abs(arr[i] - arr[i - j]);
                  min_energy = Math.min(min_energy, jump);
              }
          }
          dp[i]=min_energy;
      }
      return dp[dp.length-1];
    }
```
# Complexities

Time:O(n)

Space:O(n)

