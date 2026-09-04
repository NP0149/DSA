[Problem Link](https://leetcode.com/problems/edit-distance/description/)

# recurrsion

```
class Solution {
    int find(String s1,String s2,int indx1,int indx2){
        if(indx1<0){
            return indx2+1;
        }
        if(indx2<0){
            return indx1+1;
        }
        if(s1.charAt(indx1)==s2.charAt(indx2)){
            return find(s1,s2,indx1-1,indx2-1);
        }
        int insert=1+find(s1,s2,indx1,indx2-1);
        int delete=1+find(s1,s2,indx1-1,indx2);
        int replace=1+find(s1,s2,indx1-1,indx2-1);
        return Math.min(insert,Math.min(delete,replace));
    }
    public int minDistance(String s1, String s2) {
        int indx1=s1.length()-1;
        int indx2=s2.length()-1;
        return find(s1,s2,indx1,indx2);
    }
}
```

# Memoisation

```
class Solution {
    int find(String s1,String s2,int indx1,int indx2,int dp[][]){
        if(indx1<0){
            return indx2+1;
        }
        if(indx2<0){
            return indx1+1;
        }
        if(dp[indx1][indx2]!=-1){
            return dp[indx1][indx2];
        }
        if(s1.charAt(indx1)==s2.charAt(indx2)){
            return dp[indx1][indx2]=find(s1,s2,indx1-1,indx2-1,dp);
        }
        int insert=1+find(s1,s2,indx1,indx2-1,dp);
        int delete=1+find(s1,s2,indx1-1,indx2,dp);
        int replace=1+find(s1,s2,indx1-1,indx2-1,dp);
        return dp[indx1][indx2]=Math.min(insert,Math.min(delete,replace));
    }
    public int minDistance(String s1, String s2) {
        int indx1=s1.length()-1;
        int indx2=s2.length()-1;
        int dp[][]=new int[s1.length()][s2.length()];
        for(int i=0;i<s1.length();i++){
            Arrays.fill(dp[i],-1);
        }
        return find(s1,s2,indx1,indx2,dp);
    }
}
```
# tabulation
```
class Solution {
    public int minDistance(String s1, String s2) {
        int dp[][]=new int[s1.length()+1][s2.length()+1];
        for(int i=0;i<=s1.length();i++){
            dp[i][0]=i;
        }
        for(int i=0;i<=s2.length();i++){
            dp[0][i]=i;
        }
        for(int i=1;i<=s1.length();i++){
            for(int j=1;j<=s2.length();j++){
                if(s1.charAt(i-1)==s2.charAt(j-1)){
                    dp[i][j]=dp[i-1][j-1];
                }
                else{
                    int insert=1+dp[i][j-1];
                    int delete=1+dp[i-1][j];
                    int replace=1+dp[i-1][j-1];
                    dp[i][j]=Math.min(insert,Math.min(delete,replace));
                }
            }
        }
        return dp[s1.length()][s2.length()];
    }
}
```
