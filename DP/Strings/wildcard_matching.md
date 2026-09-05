# Wildcard matching

# Recurrsive

```
class Solution {
    boolean find(String s,String t,int indx1,int indx2){
        if(indx1<0 && indx2<0){
            return true;
        }
        if(indx1<0 && indx2>=0){
            for(int i=indx2;i>=0;i--){
                if(t.charAt(i)!='*'){
                    return false;
                }
            }
            return true;
        }
        if(indx2<0){
            return false;
        }
        if(t.charAt(indx2)=='*'){
           return (find(s,t,indx1-1,indx2) || find(s,t,indx1,indx2-1));
        }
        if(s.charAt(indx1)==t.charAt(indx2) || t.charAt(indx2)=='?'){
            return find(s,t,indx1-1,indx2-1);
        }
       return false;
    }
    public boolean isMatch(String s, String t) {
        return find(s,t,s.length()-1,t.length()-1);
    }
}
```
# Memoisation

```
class Solution {
    int find(String s,String t,int indx1,int indx2,int dp[][]){
        if(indx1<0 && indx2<0){
            return 1;
        }
        if(indx1<0 && indx2>=0){
            for(int i=indx2;i>=0;i--){
                if(t.charAt(i)!='*'){
                    return 0;
                }
            }
            return 1;
        }
        if(indx2<0){
            return 0;
        }
        if(dp[indx1][indx2]!=-1){
            return dp[indx1][indx2];
        }
        if(t.charAt(indx2)=='*'){
           return dp[indx1][indx2]=(find(s,t,indx1-1,indx2,dp)==1 || find(s,t,indx1,indx2-1,dp)==1)?1:0;
        }
        if(s.charAt(indx1)==t.charAt(indx2) || t.charAt(indx2)=='?'){
            return dp[indx1][indx2]=(find(s,t,indx1-1,indx2-1,dp)==1)?1:0;
        }
       return dp[indx1][indx2]=0;
    }
    public boolean isMatch(String s, String t) {
        int dp[][]=new int[s.length()][t.length()];
        for(int i=0;i<s.length();i++){
            Arrays.fill(dp[i],-1);
        }
        return (find(s,t,s.length()-1,t.length()-1,dp)==1)?true:false;
    }
}
```

# Tabulation

```
class Solution {
    public boolean isMatch(String s, String p) {
        int dp[][]=new int[s.length()+1][p.length()+1];
        dp[0][0]=1;
        for(int i=1;i<=p.length();i++){
           if(p.charAt(i-1)=='*'){
            dp[0][i]=dp[0][i-1];
           }
           else{
            dp[0][i]=0;
           }
        }
               
       for(int i=1;i<=s.length();i++){
        for(int j=1;j<=p.length();j++){
            if(s.charAt(i-1)==p.charAt(j-1) || p.charAt(j-1)=='?'){
                dp[i][j]=dp[i-1][j-1];
            }
            else if(p.charAt(j-1)=='*'){
                dp[i][j]=(dp[i-1][j]==1 || dp[i][j-1]==1)?1:0;
            }
        }
       }
       return dp[s.length()][p.length()]==1;
    }
}
```
