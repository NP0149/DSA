# Grid Path

## Usual method

```
class Solution {
    static int pathcount(int m,int n){
         if(m<0 || n<0){
            return 0;
        }
        if(m==0 && n==0){
            return 1;
        }
        int right=pathcount(m-1,n);
        int down=pathcount(m,n-1);
        return right+down;
    }
    public int uniquePaths(int m, int n) {
       return pathcount(m-1,n-1);
    }
}
```

## Complexity Analysis

Time:O(2^(m+n))

Space:O(m+n)

## Memoization

```
class Solution {
    static int find(int dp[][],int m,int n){
        if(m==0 && n==0){
            return 1;
        }
        if(m<0 || n<0){
            return 0;
        }
        if(dp[m][n]!=-1){
            return dp[m][n];
        }
        int right=find(dp,m-1,n);
        int down=find(dp,m,n-1);
        return dp[m][n]=right+down;
    }
    public int uniquePaths(int m, int n) {
        int dp[][]=new int[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                dp[i][j]=-1;
            }
        }
    return find(dp,m-1,n-1);  
    }
}
```
## Complexities

Time:O(m*n)

Space:O(m*n)+O(m+n)

## Tabulation

```
class Solution {
    static int find(int dp[][],int m,int n){
        for(int i=0;i<n;i++){
            dp[0][i]=1;
        }
        for(int j=0;j<m;j++){
            dp[j][0]=1;
        }
        for(int i=1;i<m;i++){
            for(int j=1;j<n;j++){
                dp[i][j]=dp[i-1][j]+dp[i][j-1];
            }
        }
        return dp[m-1][n-1];
    }
    public int uniquePaths(int m, int n) {
        int dp[][]=new int[m][n];
        for(int i=0;i<m;i++){
            for(int j=0;j<n;j++){
                dp[i][j]=0;
            }
        }
        return find(dp,m,n);
    }
}
```

## Complexities

Time:O(m*n)

Space:O(m*n)

## Optimal Appoarch

```
class Solution {
    public int uniquePaths(int m, int n) {
      int dp[]=new int[n];
      for(int i=0;i<n;i++){
        dp[i]=1;
      }
      for(int i=1;i<m;i++){
        for(int j=1;j<n;j++){
            dp[j]=dp[j]+dp[j-1];
        }
      }
      return dp[n-1];
    }
}
```
## Complexities

Time:O(m*n)

Space:O(n)
