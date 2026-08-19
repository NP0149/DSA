# Longest common subsequence

[Problem Link](https://www.geeksforgeeks.org/problems/longest-common-subsequence-1587115620/1)

# Using recurrsion

```
class Solution {
    static int find_rec(String s1,String s2,int indx1,int indx2){
        if(indx1<0 || indx2<0){
            return 0;
        } 
        if(s1.charAt(indx1)==s2.charAt(indx2)){
            return 1+find_rec(s1,s2,indx1-1,indx2-1);
        }
        return Math.max(find_rec(s1,s2,indx1-1,indx2),find_rec(s1,s2,indx1,indx2-1));
        
    }
    public int lcs(String s1, String s2) {
        // code here
        int indx1=s1.length()-1;
        int indx2=s2.length()-1;
        return find_rec(s1,s2,indx1,indx2);
    }
}
```

# Using memoisation

```
class Solution {
    static int find_rec(String s1,String s2,int indx1,int indx2,int [][]dp){
        if(indx1<0 || indx2<0){
            return 0;
        } 
        if(dp[indx1][indx2]!=-1){
            return dp[indx1][indx2];
        }
           if(s1.charAt(indx1)==s2.charAt(indx2)){
            return dp[indx1][indx2]=1+find_rec(s1,s2,indx1-1,indx2-1,dp);
        }
        return dp[indx1][indx2]=Math.max(find_rec(s1,s2,indx1-1,indx2,dp),find_rec(s1,s2,indx1,indx2-1,dp));
    }
    public int lcs(String s1, String s2) {
        // code here
        int indx1=s1.length()-1;
        int indx2=s2.length()-1;
        int dp[][]=new int[s1.length()][s2.length()];
        for(int arr[]:dp){
            Arrays.fill(arr,-1);
        }
        return find_rec(s1,s2,indx1,indx2,dp);
    }
}
```
# Tabulation

```
class Solution {
    public int lcs(String s1, String s2) {
   int m=s1.length();
   int n=s2.length();
   
   int dp[][]=new int[m+1][n+1];
   
   for(int i=1;i<=m;i++){
       for(int j=1;j<=n;j++){
           if(s1.charAt(i-1)==s2.charAt(j-1)){
               dp[i][j]=1+dp[i-1][j-1];
           }
           else{
               dp[i][j]=Math.max(dp[i-1][j],dp[i][j-1]);
           }
       }
   }
   return dp[m][n];
        
    }
}
```
