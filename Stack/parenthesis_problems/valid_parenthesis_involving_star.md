# valid parenthesis involving star

[Problem Link](https://leetcode.com/problems/valid-parenthesis-string/?envType=daily-question&envId=2026-10-04)


```
class Solution {

    boolean find(String s,int indx,int count,int dp[][]){
        if(count<0){
            return false;
        }
       if(indx==s.length()){
        return count==0;
       }
       if(dp[indx][count]!=-1){
        return dp[indx][count]==1;
       }
        char curr=s.charAt(indx);
         boolean result=false;
        if(curr=='('){
            result=find(s,indx+1,count+1,dp);
        }
        else if(curr==')'){
            result=find(s,indx+1,count-1,dp);
        }
        else{
        boolean open=find(s,indx+1,count+1,dp);
        boolean close=find(s,indx+1,count-1,dp);
        boolean ntg=find(s,indx+1,count,dp);
        result=open || close || ntg;
        }
       dp[indx][count]=(result==true)?1:0;
       return dp[indx][count]==1;
    }
    public boolean checkValidString(String s) {
     int dp[][]=new int[s.length()][s.length()];
     for(int arr[]:dp){
        Arrays.fill(arr,-1);
     }
       return find(s,0,0,dp);
    }
}
```
