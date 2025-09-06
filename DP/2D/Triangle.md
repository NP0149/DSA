# Triangle 

[Problem Link](https://leetcode.com/problems/triangle/)


# Usual Recurrsion

```
class Solution {
    static int find(List<List<Integer>> tri,int n,int i,int j){
        if(i==n-1){
            return tri.get(i).get(j);
        }
        int right=find(tri,n,i+1,j+1);
        int down=find(tri,n,i+1,j);
        return Math.min(right,down)+tri.get(i).get(j);
    }
    public int minimumTotal(List<List<Integer>> tri) {
        int n=tri.size();
        int i=0;
        int j=0;
        return find(tri,n,i,j) ;                   
    }
}
```

# Complexity Analysis

Time:O(n^2)

Space:O(n^2)

# Memoization

```
class Solution {
    static int find(List<List<Integer>> li,int m,int i,int j,int dp[][]){
      if(i==m-1){
        return dp[i][j]=li.get(i).get(j);
      }
        if(dp[i][j]!=-1){
            return dp[i][j];
        }
        int right=find(li,m,i+1,j+1,dp);
        int down=find(li,m,i+1,j,dp);
        return dp[i][j]=Math.min(right,down)+li.get(i).get(j);
    }
    public int minimumTotal(List<List<Integer>> tri) {
        int m=tri.size();
        int dp[][]=new int[m][m];
        for(int i=0;i<m;i++){
            for(int j=0;j<m;j++){
                dp[i][j]=-1;
            }
        }
        return find(tri,m,0,0,dp);
    }
}
```

# Complexity Analysis

Time:O(m^2)

Space:O(m^2)


# Tabulation

```
class Solution {
    public int minimumTotal(List<List<Integer>> tri) {
        int m=tri.size();
        int dp[][]=new int[m][m];
        for(int i=0;i<m;i++){
            dp[m-1][i]=tri.get(m-1).get(i);
        }
        for(int i=m-2;i>=0;i--){
            for(int j=0;j<=i;j++){
                dp[i][j]=Math.min(dp[i+1][j+1],dp[i+1][j])+tri.get(i).get(j);
            }
        }
  return dp[0][0];
    }
}
```
# Complexity Analysis

Time:O(m^2)

Space:O(m^2)

# Optimised

```
class Solution {
    public int minimumTotal(List<List<Integer>> tri) {
        int m=tri.size();
        int dp[]=new int[m];
        for(int i=0;i<m;i++){
            dp[i]=tri.get(m-1).get(i);
        }
        for(int i=m-2;i>=0;i--){
            for(int j=0;j<=i;j++){
                dp[j]=Math.min(dp[j],dp[j+1])+tri.get(i).get(j);
            }
        }
        return dp[0];
    }
}
```

# Complexity Analysis

Time:O(m^2)

Space:O(m);

